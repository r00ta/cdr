# codewars-cli

> TODO: Rename project to `codewars-compiler`, `codewars-cli-runner` or something that is less ambiguous. 

This is the command-line utility used by [Codewars](http://www.codewars.com) to execute code snippets of various languages,
using various testing frameworks.

You can run `node run --help` to view information about which arguments are supported.

## Purpose

The purpose of this project is to provide a low level ability to run "Kata". This tool will eventually be used by both
the codewars.com sandboxing processes as well as used by developers locally so that they can do kata offline.

A key advantage to having this tool open sourced is that it becomes possible for the Codewars community to contribute support for new languages and frameworks. By simply adding new languages to this tool, the majority of the work will be done and it will become much easier to support the new language on Codewars.com. 

## Supported Languages and Testing Frameworks

- JavaScript
    - mocha (comming soon...)
    - codewars

- CoffeeScript
    - mocha (comming soon...)
    - codewars

- Ruby
    - rspec (comming soon...)
    - codewars

- Python
    - unittest (comming soon...)
    - codewars (comming soon...)

## Examples:

### Basic Usage
If you just wanted to execute some code and return its output, you can do so like the following:

#### Ruby
```
node run -l ruby -c "puts 123"
```

#### JavaScript
```
node run -l js -c "console.log(123)"
```

### Kata Usage
You can also provide a test fixture to be ran along with the code. The output returned is the same output that is parsed
by Codewars to render its kata output.

#### Ruby
```
node run -l ruby -c "a = 1" -f "Test.expect a == 1"
```

#### JavaScript
```
node run -l js -c "a = 1" -f "Test.expect(a == 1)"
```

## Docker

The cli now supports running inside a docker container for better isolation.

#### Build
```
docker build -t codewars/cli-runner .
```

#### Run Help
```
docker run --rm codewars/cli-runner --help
```

#### Run JavaScript Kata
```
docker run --rm codewars/cli-runner -l js -c "a = 1" -f "Test.expect(a == 1)"
```

#### Run Ruby Kata
```
docker run --rm codewars/cli-runner -l ruby -c "a = 1" -f "Test.expect a == 1"
```

### Vagrant

> Version 1.6.3 or higher is required.

 A fully working environment is provided via Vagrant. These steps will get a working server running:
 ```
 vagrant up
 vagrant ssh
 supervisor /vagrant/server.js
 ```

 You should now have a fully working server with Docker support. You can access the server using `localhost:8080'.
