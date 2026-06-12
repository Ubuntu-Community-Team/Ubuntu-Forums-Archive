---
title: "D programming"
date: 2007-10-24
forum: The Cafe
---

### Post by proalan on 2007-10-24
Anyone heard about this new programming language D?

[http://en.wikipedia.org/wiki/D_programming_language](http://en.wikipedia.org/wiki/D_programming_language)

what next D++?

---

### Post by mikeypizano on 2007-10-24
All I can say is wow. I thought that C++ was confusing!
```

#!/usr/bin/dmd -run
/* sh style script syntax is supported! */
/* Hello World in D
 * To compile:
 *   dmd hello.d
 * or to optimize:
 *   dmd -O -inline -release hello.d
 * or to get generated documentation:
 *   dmd hello.d -D
 */
 
import std.stdio;                        // References to  commonly used I/O routines.
alias char[] string;    // for compatibility with older compilers; newer compilers define this implicitly
 
int main(string[] args)                 
{
    // 'writefln' (Write-Formatted-Line) is the type-safe 'printf'
    writefln("Hello World, "             // automatic concatenation of string literals
             "Reloaded");
 
    // Strings are denoted as a dynamic array of chars 'char[]', aliased as 'string'
    // auto type inference and built-in foreach
    foreach(argc, argv; args)
    {
        auto cl = new CmdLin(argc, argv);                    // OOP is supported
        writefln(cl.argnum, cl.suffix, " arg: %s", cl.argv);       // user-defined class properties.
 
        delete cl;                   // Garbage Collection or explicit memory management - your choice
    }
 
    // Nested structs, classes and functions
    struct specs
    {
        // all vars automatically initialized to 0 at runtime
        int count, allocated;
        // however you can choose to avoid array initialization
        int[10000] bigarray = void;
    }
 
    specs argspecs(string[] args)
    // Optional (built-in) function contracts.
    in
    {
        assert(args.length > 0);                   // assert built in
    }
    out(result)
    {
        assert(result.count == CmdLin.total);
        assert(result.allocated > 0);
    }
    body
    {
        specs* s = new specs;
        // no need for '->'
        s.count = args.length;  // The 'length' property is number of elements.
        s.allocated = typeof(args).sizeof; // built-in properties for native types
        foreach(arg; args)
            s.allocated += arg.length * typeof(arg[0]).sizeof;
        return *s;
    }
 
    // built-in string and common string operations, eg. '~' is concatenate.
    string argcmsg  = "argc = %d";
    string allocmsg = "allocated = %d";
    writefln(argcmsg ~ ", " ~ allocmsg,
            argspecs(args).count,argspecs(args).allocated);
    return 0;
}
 
/**
 * Stores a single command line argument.
 */
class CmdLin
{
    private
    {
        int _argc;
        string _argv;
        static uint _totalc;
    }
 
    public:
        /**
         * Object constructor.
         * params:
         *   argc = ordinal count of this argument.
         *   argv = text of the parameter
         */
        this(int argc, string argv)
        {
            _argc = argc + 1;
            _argv = argv;
            _totalc++;
        }
 
        ~this() // Object destructor
        {
            // Doesn't actually do anything for this example.
        }
 
        int argnum() // A property that returns arg number
        {
            return _argc;
        }
 
        string argv() // A property that returns arg text
        {
            return _argv;
        }
 
        wstring suffix() // A property that returns ordinal suffix
        {
            wstring suffix; // Built in Unicode strings (UTF-8, UTF-16, UTF-32)
            switch(_argc)
            {
                case 1:
                    suffix = "st";
                    break;
                case 2:
                    suffix = "nd";
                    break;
                case 3:
                    suffix = "rd";
                    break;
                default:  // 'default' is mandatory with "-w" compile switch.
                    suffix = "th";
            }
            return suffix;
        }
 
        /**
          * A static property, as in C++ or Java,
          * applying to the class object rather than instances.
          * returns: The total number of commandline args added.
          */
        static typeof(_totalc) total()
        {
            return _totalc;
        }
 
        // Class invariant, things that must be true after any method is run.
        invariant ()
        {
            assert(_argc > 0);
            assert(_totalc >= _argc);
        }
}

```

---

### Post by curuxz on 2007-10-24
> **mikeypizano said:**
> All I can say is wow. I thought that C++ was confusing!
```

#!/usr/bin/dmd -run
/* sh style script syntax is supported! */
/* Hello World in D
 * To compile:
 *   dmd hello.d
 * or to optimize:
 *   dmd -O -inline -release hello.d
 * or to get generated documentation:
 *   dmd hello.d -D
 */
 
import std.stdio;                        // References to  commonly used I/O routines.
alias char[] string;    // for compatibility with older compilers; newer compilers define this implicitly
 
int main(string[] args)                 
{
    // 'writefln' (Write-Formatted-Line) is the type-safe 'printf'
    writefln("Hello World, "             // automatic concatenation of string literals
             "Reloaded");
 
    // Strings are denoted as a dynamic array of chars 'char[]', aliased as 'string'
    // auto type inference and built-in foreach
    foreach(argc, argv; args)
    {
        auto cl = new CmdLin(argc, argv);                    // OOP is supported
        writefln(cl.argnum, cl.suffix, " arg: %s", cl.argv);       // user-defined class properties.
 
        delete cl;                   // Garbage Collection or explicit memory management - your choice
    }
 
    // Nested structs, classes and functions
    struct specs
    {
        // all vars automatically initialized to 0 at runtime
        int count, allocated;
        // however you can choose to avoid array initialization
        int[10000] bigarray = void;
    }
 
    specs argspecs(string[] args)
    // Optional (built-in) function contracts.
    in
    {
        assert(args.length > 0);                   // assert built in
    }
    out(result)
    {
        assert(result.count == CmdLin.total);
        assert(result.allocated > 0);
    }
    body
    {
        specs* s = new specs;
        // no need for '->'
        s.count = args.length;  // The 'length' property is number of elements.
        s.allocated = typeof(args).sizeof; // built-in properties for native types
        foreach(arg; args)
            s.allocated += arg.length * typeof(arg[0]).sizeof;
        return *s;
    }
 
    // built-in string and common string operations, eg. '~' is concatenate.
    string argcmsg  = "argc = %d";
    string allocmsg = "allocated = %d";
    writefln(argcmsg ~ ", " ~ allocmsg,
            argspecs(args).count,argspecs(args).allocated);
    return 0;
}
 
/**
 * Stores a single command line argument.
 */
class CmdLin
{
    private
    {
        int _argc;
        string _argv;
        static uint _totalc;
    }
 
    public:
        /**
         * Object constructor.
         * params:
         *   argc = ordinal count of this argument.
         *   argv = text of the parameter
         */
        this(int argc, string argv)
        {
            _argc = argc + 1;
            _argv = argv;
            _totalc++;
        }
 
        ~this() // Object destructor
        {
            // Doesn't actually do anything for this example.
        }
 
        int argnum() // A property that returns arg number
        {
            return _argc;
        }
 
        string argv() // A property that returns arg text
        {
            return _argv;
        }
 
        wstring suffix() // A property that returns ordinal suffix
        {
            wstring suffix; // Built in Unicode strings (UTF-8, UTF-16, UTF-32)
            switch(_argc)
            {
                case 1:
                    suffix = "st";
                    break;
                case 2:
                    suffix = "nd";
                    break;
                case 3:
                    suffix = "rd";
                    break;
                default:  // 'default' is mandatory with "-w" compile switch.
                    suffix = "th";
            }
            return suffix;
        }
 
        /**
          * A static property, as in C++ or Java,
          * applying to the class object rather than instances.
          * returns: The total number of commandline args added.
          */
        static typeof(_totalc) total()
        {
            return _totalc;
        }
 
        // Class invariant, things that must be true after any method is run.
        invariant ()
        {
            assert(_argc > 0);
            assert(_totalc >= _argc);
        }
}

```

To be fair they are using lots of comments to explain things exactly.

I think I will stick to web programming in PHP i have enough of a headache already :)

---

### Post by mikeypizano on 2007-10-24
I meant all the indenting and stuff. I just found this on digg:
[http://arstechnica.com/news.ars/post/20071023-microsoft-to-push-functional-programming-into-the-mainstream-with-f.html](http://arstechnica.com/news.ars/post/20071023-microsoft-to-push-functional-programming-into-the-mainstream-with-f.html)

---

