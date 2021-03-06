pywalk: A Python AST walker
===========================

`pywalk` allows you to specify a function that will walk over a Python abstract
syntax tree in Racket, with its structure as defined in the `pysx` ([Python to
S-Expressions](https://github.com/mattmight/python-to-sexp)) tool.



Installation
------------

To install, use:

```
$ raco pkg install
```


To do a site-wide install for all users, use:

```
$ sudo raco pkg install --scope installation
```


Usage
-----

To import the package, use:

```
(require pywalk)
```


### Top-down transformation

To transform all statements in a module once, use:

```
 (walk-module <module> #:transform-stmt <transformer>)
```

To repeatedly transform the statements in a module until the module stops changing, use:

```
 (walk-fix <module> #:transform-stmt <transformer>)
```

A `<transformer>` needs to meet the following specification:

```
 <transformer> : <stmt> -> list of <stmt>
```

That is, a transformer can convert a single statement into several statements.

By default, the transformation is applied top-down.


### Bottom-up transformation

To transform statements in a bottom-up fashion, use the `#:transform-stmt/bu`
parameter instead.





TODO
----

Change `walk-fix` to `walk-module/fix`.
