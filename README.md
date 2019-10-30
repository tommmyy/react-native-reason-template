This repo was created with following trials and errors according to official instructions.

# Running a project

One window:

```sh
yarn ios

# or

yarn android
```

Second window:

```sh
yarn re:watch
```

# Main source of instructions:

- [React-navive-cli](https://reasonml-community.github.io/reason-react-native/en/docs/install/#create-a-new-project-with-reason-react-native)
- [Reason ML platfrorm](https://bucklescript.github.io/)

# My take

For Mac - install (!!!) XCode 11 and OpenJDK8
For Android - ??

Using Node v10.10.0

## Installing tools

```
yarn global add react-native-cli bs-platform --ignore-engines
```

## Create project

This should work, but for me it did not:

```sh
react-native init RNRTemplate --template reason-react-native-template
```

So I needed to create Reason project manually.

1. create repo
```sh
react-native init RNRTemplate
cd RNRTemplate
yarn add bs-platform --dev && yarn add reason-react reason-react-native
```

2. Add following lines to `.gitignore`:

```
# Reason

*.bs.js
.bsb.lock
.merlin
lib/bs
```

3. Then I add scripts to `package.json` for working with ReasonML compilation:

```
"scripts": {
		"re:build": "bsb -clean-world -make-world",
    "re:watch": "bsb -clean-world -make-world -w",
		...
}
```

4. Lastly you need create a file `bsconfig.json` to configure bucklescript.

```json
{
  "name": "demo-react-native-app",
  "refmt": 3,
  "reason": {
    "react-jsx": 3
  },
  "package-specs": {
    "module": "es6",
    "in-source": true
  },
  "suffix": ".bs.js",
  "sources": [
    {
      "dir": "src",
      "subdirs": true
    }
  ],
  "bs-dependencies": ["reason-react", "reason-react-native"]
}
```

# Result
Result is this repo.


