---
title: "Two reasons to learn how to code, and two ways to learn"
date: 2018-12-02
forum: Tutorials
---

### Post by freemedia2018 on 2018-12-02
The more obvious reason to learn how to code is to help with your career. This is a great reason, But I don't think it's the best reason.

The best reason to learn how to code is that it will help you understand computers. If you use computers at all (you probably do if you're reading this forum) then coding will enrich your experience. There are other situations that make understanding computers vital (note that I said understanding computers, not understanding "applications") and coding will help with that as well.

Knowing how to code makes all computers far more similar. It may not be obvious to everyone why this is so, but code is typically an abstraction that applies to (and is more representative of) virtually all modern computers and quite a few decades-old computers.

Here is a slightly oversimplified idea of where code is in terms of abstraction:

```
Applications (made of code)
     |
Higher-level code
     |
Lower-level code
     |
Hardware

```

The difference between higher-level code and lower-level code is that lower-level code is conceptually closer to what the hardware actually does. Higher level code maps 1:1 to lower-level code, but is more abstract (and easier for more people to work with, regardless of what hardware they use.) It also runs on a wider variety of hardware. Higher-level code is easier to maintain, though higher and lower-level code ultimately work together to make the computer run.

You can still express lower level coding concepts in higher level code, so even if you learn something easy, you might understand more concepts of lower level coding than you realise. Lower level coding includes tasks like copying values, comparing values, performing calculations, and moving to other instructions based on the comparison of values. In a more abstract way, these are also tasks that you will learn when you do higher level coding.

If your goal is career-based programming, there are a number of organisations and businesses that exist to help train you. You may find this is less expensive (and faster) than going to school for it.

But if your goal is simply to be able to understand how to code, you have a lot more leeway. You do not need to make it difficult. Contrary to what famous computer pioneer Edsger Dijkstra said, learning the wrong language first will most certainly not taint your education for life (Dijkstra knew a great deal about computers and we are in his debt, but he understood less about pedagogy. Also a few of his most famous remarks were peddled a bit sensationally, and he can't be blamed for that.)

For those who want coding as a way to better understand computers, the fundamentals are enough to get you started.

A popular idea lately is that you should think of a project you want to accomplish, and then set out to work on it. This is a good start for some people, but how do you know what you'll be able to code if you don't understand the very basics? Some of it you will be able to pick up along the way, if you "start in the middle."

If you start in the middle and you do alright, it's fine to try-- you may find you are ahead this way. I have watched several people try this and then find they still lack a basic understanding, which they find is a source of frustration that keeps them from moving forward. So for most people, I would say "when you start to find it difficult, go and learn the basics."

Note I spent 25 years working with BASIC, one of the easiest-to-learn languages of all time. I also code in Javascript, Bash and Python. BASIC was a language heavily criticised by Dijkstra, though it has to be mentioned that the version of BASIC he was criticising lacked many of the features of "Structured Programming" that Dijkstra promoted-- which are present in many versions of BASIC from the mid 1980s onward. BASIC itself dates back to 1964.

So what are the basics of programming? First of all, I am not going to introduce you to the GOTO command. This isn't to malign it, GOTO (also known as JMP) is a vital CPU instruction and thus can't be all bad, but (due in part to Dijkstra) today it is more common to use other forms of branching in higher-level languages. Instead I will show you loops, functions and conditionals.

The basics that I tend to focus on when teaching people are:

1. Variables 2. Input 3. Output 4. Basic math 5. Loops 6. Conditionals 7. Functions

And while some features are different in subtle, though sometimes important ways, most of these features exist in most modern languages.

If you are using Ubuntu, or a distro in a similar family, you already have 3 programming environments worth mentioning:

1. Bash -- when you sudo apt-get install, you are using the sudo and apt-get commands from a Bash environment. You can program in this (I've even implemented a small programming language or two in Bash.)

2. JavaScript -- Ubuntu comes with a web browser that supports Javascript. While it is mostly used for websites, Javascript makes it possible to emulate other forms of software using asm.js for example. The internet archive has DOS emulators implemented in JavaScript. It has evolved into a very powerful language.

3. Python -- Ubuntu relies on Python for a number of tasks, and it comes pre-installed. Python is a great language for education, and is also used in industry. It is now developed at Google, and it can be found running behind many websites, including YouTube.

The purpose of this quick article will be to demonstrate variables, input/output, basic math, loops, conditionals and functions in these three languages.

VARIABLES

A variable can be set in bash from the command line, like this:

```
p="hello world"
```

To "reference" or use that variable, simply put a dollar sign in front of it: $p. We will demonstrate this in a moment. This also works in Python and JavaScript, but unlike Bash, you can have spaces between the p and =, and between the = and quotes:

```
p = "hello world"
```

That is valid in Python and JavaScript, not in Bash.

JavaScript also requires that you complete the line with a semicolon like this:

```
p = "hello world" ;
```

In Bash and Python, this is optional -- and also allows you to put multiple commands on a single line.

Don't worry if you cant learn all three languages at once, just get a feel for the one you prefer for now and feel free to skip the comparisons between the 3 languages. Alternatively, you may enjoy the comparison. Learning just one language is far better than avoiding the subject.

In JavaScript and Python, you can reference a variable without the dollar sign. This will be demonstrated in the section on output.

```
BASH: p="hello world"
JS: p = "hello world" ;
PYTHON: p = "hello world"
```

INPUT

JavaScript does make it possible to get input from the mouse and keyboard in a way that seems "direct", such as keypresses and the position and actions of the mouse. For touchscreens, the digitiser is functionally a mouse. More common than this however is for JavaScript to get input from HTML forms and buttons.

In that event (pun not intended) "input" is about reading information from the form elements as attributes of those elements. You can give a textbox an id, and then set a variable to "id.value" to get the input. This is not the now conventional or "proper" way to get the value, but it does traditionally and commonly work.

If you are learning JavaScript, you may notice challenges that make it a great second language to learn but in my opinion, it makes a terrible first language (at least when aimed at all beginners) because it can make things so tedious at times. Then again, it is available on practically every computer, and some very powerful things can be done with it with surprisingly little work. (If every gui was as easy to code as JavaScript and HTML forms, that would be great.)

For comparison, getting keyboard input in Bash is simply:

```
read p
```

That's it! In Python, it is either:

```
p = input()
```

or:

```
p = raw_input()
```

This depends on what version of Python you use. raw_input() is for Python 2.

OUTPUT

It is somewhat pointless to have the computer do something if it can't either store or at least tell someone what the result was. Such processeses constitute output.

Output is generally aimed at a particular device-- the screen, usb drive, speakers, the modem or network device. Network devices work with both input and output-- as do touchscreens, although touchscreens are really an input device stacked on top of an output device (the digitiser and screen.)

```
BASH: echo "hello, $p"
```

This says "hello," and the contents of variable $p on the screen. You can also use this to get other information from the operating system, for example, if you say

```
echo $PATH
```

This will tell you the list of folders that the operating system looks in to find commands that you run without specifying the location. For a list of such variables available to you, use the env command:

```
env
```

```
PYTHON: print("hello", p)
```

In Python 2, these parentheses for the print command are optional.

Javascript lets you output data directly to the page like this:

```
document.write(p);
```

It has to be said that when I introduce JavaScript, I do not take a "best practices" approach. That would be better for career programmers, whose job it is to find a class that will train them in practices that are relevant to an industry.

Rather, I take an approach that makes it easy to learn programming concepts. Often you will hear "learning to code isn't about the language" but they proceed to teach you the "best" way to use a specific language. If the best way is more complicated, I believe this loses potential beginners who might never realise that programming can be fun and easy. Best practices change with trends, though some are long-lasting.

Anything that is not strictly necessary that makes a beginner give up before they need to should be questioned when introducing programming concepts for the first time. It's really ok to build up the quality of your skills gradually-- even Linus Torvalds started with GOTO. It often isn't fun or easy if you code for a living. But you don't need the same skills to get tasks done and enjoy doing research that you would need for writing code for a paycheck.

Tags like this in HTML:

```
<span id="nameoftheid"></span>
```

Allow you to define arbitrary sections of page that can be written to and read from, and modified by setting a variable to nameoftheid.innerHTML and then changing its contents. As you set nameoftheid.innerHTML to something else, the contents change on the page as well. This is good for both input and output.

BASIC MATH

```
PYTHON: x = x + 2
JS: x = x + 2;
BASH: x=$(($x+2))
```

To the computer, all things are numeric. The space between each word is equivalent to "32" (first through the ASCII standard, and also in Unicode) and an upppercase "A" is 65. If you add 32 to "A" you get a lowercase "a", or 97.

Coders are aware of these relationships, though very few people memorise them. To work with an uppercase "A" you typically just type it out. There are situations where you want to look up some of the values you wish to process, but this is not the sort of thing that typical programmers do all day. At least, not in many years.

Most average-level programming is less math-centric than early programming was. Developing algorithms is heavily math-oriented, though so much of what constitutes modern programming is simply using existing algorithms. If you are good at math, it will help a lot. If you are not good at math, it does not mean you can't write programs.

Basic arithmetic at least, is vital at times. There are many fields of coding where higher math is also useful.

There is another side to that, however. If you are writing a Bash script to help you accomplish some simple tasks, you may not really use math at all--- other than a bit of counting. The math operator in Bash is terrible-- it doesn't even perform division on fractions or decimals. If you want your bash script to do real math, try calling bc or python -c from Bash:

```
n=7 ; d=5
p=$(python -c "print float($n)/$d")
echo $p
```

Note that Python 2 requires one of the values to be a "float" to do "floating point" division. "Floating point" means the decimal moves. They could have just called it "moving decimal" but "floating point" probably sounds cooler.

The code here is only redundant in a technical sense. It demonstrates both setting a variable to a value and outputting it, even though python -c "print 7.0/5" by itself would give the same output as this more useful example.

LOOPS

I separate loops into two categories-- iterative and continuous. Distinguishing between these is somewhat superficial, but useful.

Continuous loops are normally designed to stop looping at some point. The actual loop count is arbitrary, it keeps running the same code until something happens. (Technically, iteration also loops until something happens.)

A loop in JavaScript will typically stop output from updating until the loop is done. If you are doing animation, you'll need a different way to get updates (probably involving a timer) than just setting up a loop.

In Bash, you can loop continually like this:

```
while [[ 1 ]] ; do echo "it keeps saying this" ; done
```

In Python:

```
while 1:
    print("it keeps saying this")
```

Iteration takes a set (of numbers, of items) and does the same code again, once for each item or number.

```
BASH: for p in yes no maybe ; do echo $p ; done
```

```
PYTHON: for p in ["yes", "no", "maybe"]: print(p)
```

```
JS: for (var p of ['yes', 'no', 'maybe']) { document.write(p + "\n"); }
```

You can use iteration with a set of numbers to repeat a process a certain number of items. The most common example of this is a for loop, which we just demonstrated with a group of items.

CONDITIONALS

Loops run a section of code repeatedly, and conditionals run a section of code if certain conditions are true.

```
BASH: if [[ "$p" == "hello" ]] ; then echo "hello there" ; fi
```

```
JS: if (p == "hello") { document.write("hello there"); }
```

```
PYTHON: if p == "hello": print("hello there")
```

FUNCTIONS

A function lets you define a section of code that will be run like a custom-made command. A great deal of coding is defining such routines, or calling them. For example, when Apple "invented" slide-to-unlock, they really only combined two features that were already decades old:

1. A scrollbar. Not really novel stuff at all.

2. A conditional that breaks if the scroll bar reaches its upper limit.

For people who code, this is an extremely trivial combination. Every program combines two or more (quite often thousands) of fundamental features like these, and they aren't treated as novel inventions.

You can "invent" a function that prints something twice like this:

```
JS: function writetwice(p) { document.write(p + "\n"); document.write(p + "\n"); }
```
Use the function (also known as "calling" the function) like other commands: writetwice("allo");

```
BASH: function writetwice() { p=${1} ; echo "$p" ; echo "$p" ; }
```
Use the function like this: writetwice "allo"

```
PYTHON: def writetwice(p): print("allo") ; print("allo")
```
Use the function like this: writetwice("allo")

Functions are where code is all put together. So much of coding is simply calling existing functions, giving data as "parameters" (in this example, our writetwice function took the parameter p, which we said was "allo") and looking up what sorts of parameters are acceptable input for the function.

Programmers don't usually memorise an entire programming language. If you are using a simple educational language, with only a handful of commands, then you can learn the whole language. This is one advantage of educational languages. But ultimately you are going to use larger languages that include far more functions than you will ever use. If you use features repeatedly, you will find that you have to look them up less often. But this is what programmers do.

NOT COVERED

This tutorial did not cover arrays (which I usually teach with along with variables) or data types. Bash and Javascript do not entirely distinguish between data types, they have what is called "weak typing." Python does not have weak typing, it is unambiguous with what each data type is, but Python types are dynamic so you can go for example, from a variable containing numeric data to the same variable containing the string "hello, world."

This tutorial neatly skipped over object classes, method calls (in fact it conflated function calls with method calls, because Python arguably does that as well-- much to my pleasure. Technically everything in Python is an object, but it still has calls to defined functions) and even importing libraries (which would be a great thing to cover too.) But this tutorial is long enough for a simple introduction. Hopefully it will make code more familiar and easier to learn. If you still feel like this is too complex, let me know. That's something I've spent a few years working on and these tasks can be even easier than this.

If you made it through this introduction and are disappointed that there are no "real examples," great! Either go find an intro to Python, Bash or JavaScript specifically, and learn more. You'll be very glad you did. Feel free to send me a Private Message or start a thread in the programming section if you try that and have difficulty getting started.

Programming is breaking tasks down into steps consisting of these things. Ultimately everything on the computer is more or less programming routines, function calls or "object method calls" like the ones explained here. Underneath that, between the CPU chip and the programming environment, there are deeper, slightly more esoteric details. Most coders do not use those, but they are there if you want to get deeper into the computer.

The computer is really a calculator with fancier output. Instead of just expressing the numeric output as numbers, it can express the numeric output as colour, sound, or network signals. It's still fundamentally a calculator, and you can give it fancier input too-- that is still really just numbers, except to the user and sometimes, the coder.

Happy Coding!

This article is in the Public Domain.

---

### Post by TheFu on 2018-12-03
Why learn to code? It is a survival skill for the modern world.

Lots of skills are helpful in our lives.  Understanding just a little about coding (learning 1 language to intermediate level) is similar to having a slight understanding of automobiles or home mechanics or simple electrical theory or gardening or knowing how to swim.  We don't need to be experts, but a little knowledge will help when we need to bring in more competent experts to handle problems that are incomplete skills aren't able to solve.

Any time someone with zero knowledge seeks expert advice, there is a risk of being overcharged or having totally impossible expectations.  Learning to code, even just a little, will ensure you and your children don't get "taken" multiple times in your life by computer "techs" or pretty lights on the front of some computer.  How the box looks is the least important part of a computer when you know a little about RAM, CPU, disks and networking.  Learning to program will help demystify those other things.

Learn to swim with computers - or end up paying $15K-$50K to have other people fix your computers over your life.

---

### Post by freemedia2018 on 2018-12-04
> Learning to code, even just a little, will ensure you and your children don't get "taken" multiple times in your life by computer "techs" or pretty lights on the front of some computer. How the box looks is the least important part of a computer when you know a little about RAM, CPU, disks and networking. Learning to program will help demystify those other things.

Although these are great reasons and I strongly agree, I would say that so many aspects of our lives (apart from just the workplace and convenience, but matters like privacy, safety, aspects of our lives that had a lot less to do with computer literacy beyond the use of applications until several years ago) make it vital to know these things in a way that going to a technician would scarcely substitute having personal knowledge of computers-- even if you never fix your own computer.

Often computer education tries to sidestep a fundamental understanding of computers. Teaching "computational thinking" for example, IMO is trying to teach programming while avoiding the subject. Which I think forces the student to invent conceptions that already exist, which is harder than learning them firsthand (with a little coding.)

I'm certainly not against applications, they're great-- but I do think an applications-only approach (which took hold in computer education in the 90s, and we are slowly coming out of) makes it more difficult to really understand computers, not easier. So I would have everyone learn this just to make learning every other computer concept easier. The slide-to-unlock example wasn't random, either. It's the sort of thing you only understand how trivial and non-original it is if you know what a function call is, and function calls are covered in the tutorial.

I would also point out that if the goal is truly to teach concepts, not a specific language, that you can design easier languages to teach the concepts to everyone. I am the author of such a language, and this reply is not part of the tutorial. Python is probably suitable for this, though I tried doing this with Python with people who were not required to take a class in school, and who had not decided to teach themselves-- this tool is easier for demonstrating and teaching programming in concepts in say-- a loud bar full of people, I've actually used it there.

---

