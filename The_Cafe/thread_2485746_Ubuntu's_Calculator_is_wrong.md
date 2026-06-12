---
title: "Ubuntu's Calculator is wrong ?"
date: 2023-04-07
forum: The Cafe
---

### Post by jonfisher on 2023-04-07
My friend who is a genius at math says the answer to this is 1.  Others say it is 36.  Even my Ubuntu's built in calculator says it's 36.

What gives?

---

### Post by jonfisher on 2023-04-08
I've had verification that the answer is indeed 1.

Is this not a little embarrassing that the calculator that comes with Ubuntu, even when switched to Scientific mode, comes up with the wrong answer here - ?

---

### Post by ian-weisser on 2023-04-08
Please file a proper bug report with enough detail for a developer to duplicate the issue. Since the mathematical expression seems ambiguous, expect pushback from developers.

Better yet, find a clear and unambiguous example of the calculator providing an inaccurate answer. File a bug report for that.

In your bug report, avoid offering opinions about the bug ("*Is this not a little embarrassing?*") A bug is a bug. Everybody wants the bug fixed. Stick to the facts.

---

### Post by monkeybrain20122 on 2023-04-08
It is not really the calculator's fault but the ambiguous way the question is stated, it could mean 
48 /(8*(14-8)) = 1

or 

(48/8)*(14-8) = 36

depends on where you place the brackets. 

In the jargon of the logician the question is stated in a string that is not well formed (and one reason why the notation ".|." for division is rarely used in advanced mathematics)

---

### Post by Dennis N on 2023-04-08
Rules for order of operations exist in mathematics to avoid ambiguity:

1) evaluate all expressions inside grouping symbols 
after evaluating all expresions in grouping symbols
2) evaluate multiplication and division proceeding left to right.
3) evaluate additions and subtractions proceeding left to right.
48÷8(14-8)
48÷8x6
6x6
36
The calculator is correct.

---

### Post by tea for one on 2023-04-08
Pop the following into the function bar of Libre Office Calc.
=48/8(14-8)
The response is:-
LibreOffice Calc found an error in the formula entered.
Do you want to accept the correction proposed below?
=48/8*(14-8)
Correction accepted and the answer = 36

---

### Post by Autodave on 2023-04-08
Dennis N has it correctly!  Basic math.

---

### Post by lucant on 2023-04-08
[COLOR=#000000][FONT=Liberation Serif, serif]48÷8x(14-8)
                    
                    =36[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2023-04-08
Multiplication and division have the same priority because all divisions can be written as multiplication with the inverse of the divisor (x/y=x*(1/y)), just as addition and subtraction have the same priority because subtraction can be written as adding the negative (x-y=x+(-y)) . So 48/8*6=48*0.125*6. The problem lies in leaving out the multiplication operator and assuming a higher priority because of that.

Holger

---

### Post by aljames2 on 2023-04-08
Agree, 36 it is.  Solve inside the paren first, then since all are * / , solve left to right.

---

### Post by Frogs Hair on 2023-04-08
Following the order of operations the Ubuntu calculator is correct.


    Brackets first

    Orders (i.e. Powers and Square Roots, etc.)

    Division and Multiplication (left-to-right)

    Addition and Subtraction (left-to-right)

---

### Post by #&amp;thj^% on 2023-04-08
Looks like I win...
Fun with math...lol

---

### Post by MAFoElffen on 2023-04-08
I am old. I went back to college and got 4 computer science degrees in 3 years. Plus to it was that I got to documented 32 years of working with computers.

One of the things I had to relearn, was that from my past, to the present, the rules of math precedence had changed. To what other have said here.

How it is expressed would eval to 36.

To make that expression eval to 1, you would have to express it as 
```

48/(8(14-8))

```
See attachment.

---

### Post by jonfisher on 2023-04-08
Hmm, people on the linuxquestions forum think the answer is 1

[https://www.linuxquestions.org/questions/linux-newbie-8/ubuntu%27s-calculator-is-wrong-4175723871/](https://www.linuxquestions.org/questions/linux-newbie-8/ubuntu%27s-calculator-is-wrong-4175723871/)

---

### Post by donald187 on 2023-04-08
PEMDAS baby!  Parentheses, exponents, multiplication and division in order from left to right, addition and subtraction in order from left to right.

36

---

### Post by jonfisher on 2023-04-08
My friend says this about this equation:


The full analysis of this situation is now clear: it depends on whether you think like a programmer,  or a mathematician.   C, and, through its influence over the decades, apparently many other languages as well -- clearly including Perl,as shown here -- is documented and standardized as evaluating expressions left to right, except for performing **parenthetical** expression evaluation first and bottom-up (or deepest-first).  This is just a different rule from what a mathematician or school teacher would consider the proper rules of arithmetic, namely PEMDAS.    Clearly, what's happening here is that all the participants in this discussion are programmers, who have grown up WTF commuters, physicians grown up with organic, are accustomed to the C rules and thus really do consider 36 "the right answer" because that's what the official programming language rules give you.   However, I submit that, while that is certainly the **expected result** of the calculation in a organizational language,  it is, nonetheless, **not** the "right answer" that someone who knows how to correctly perform arithmetic should get when doing the calculation  "with pencil and paper."  Outside of program source code, the rules of PEMDAS are in force and the real-world right answer is 1.  The unfortunate fact, though, is that several generations of programmers have now grown up internalizing C-style left-to-right evacuation rules, to the point where they now consistently fail to recognize that exposing that method to the outside would, such as on the display and workings of a calculator app, is a semantic error that muddies the waters and perpetuates and spreads this dangerous misperception.

If you'd like, you can add that your math-genius friend says there is **no room for argument here**: these are the facts, and their calculator apps, as they stand today are suitable only for programmers, not for the general public. For the general public, an  expression evaluator that specifically implements PEMDAS should be used instead of C-like left-to-right evaluation.  I would be happy to try to write said PEMDAS  evaluator.

The  addition of another set of parentheses forces the language to evaluate  the entire right-hand side of the division FIRST, producing a  denominator of 48 exactly as per PEMDAS.  The effect is, in essence, to  force the language/code to perfrom M before D, whereas in strict  left-to-right order, in the original expression,  the interpreter  encounters, and therefore performs, D before M.

---

### Post by lucant on 2023-04-08
Of course this is a math joke, according to the initial post the result is 36... It's a joke like...

> &#8734;+&#8734;=

---

### Post by donald187 on 2023-04-08
> **donald187 said:**
> PEMDAS baby!  Parentheses, exponents, multiplication and division in order from left to right, addition and subtraction in order from left to right.

36

Dennis N laid it out.

---

### Post by jonfisher on 2023-04-08
I'll post this from what my math friend typed, then I'll let others on here argue it out or let the thread die:

I haven't heard anything saying that mathematicians work left to right now,  **in defiance of PEMDAS**.   Certainly you work left to right if there's no need for PEMDAS -- no  parentheses, no mixing of addition and subtraction, etc.  But  mathematics, and the rules for evacuating expressions, are one thing  that absolutely ought **not to change** or "evolve over time": the rules need to be rock solid or all of math falls apart.

---

### Post by aljames2 on 2023-04-08
The distributive property can work in solving this if applied properly... that is, while following PEMDAS, and equate to the correct answer of 36.

We know multiplication & division must be performed from left to right.  You can't start in the middle and then go back to the left.  To distribute the 8 by itself implies  that we have given the multiplication (distribution) of the 8 priority over the division  operator just before it?

To use distribution it would continue as:
48 / 8(14 - 8)
= 6(14 - 8)
= 84 - 48
= 36

If instead, the problem were:
48 + 8(14 - 8)
Then we are correct to distribute the 8 first.  Of course this is a different expression than the OP, equating to 96

---

### Post by donald187 on 2023-04-08
> **jonfisher said:**
> I'll post this from what my math friend typed, then I'll let others on here argue it out or let the thread die:

I haven't heard anything saying that mathematicians work left to right now,  **in defiance of PEMDAS**.   Certainly you work left to right if there's no need for PEMDAS -- no  parentheses, no mixing of addition and subtraction, etc.  But  mathematics, and the rules for evacuating expressions, are one thing  that absolutely ought **not to change** or "evolve over time": the rules need to be rock solid or all of math falls apart.

Yeah, the multiplication and division is in order from left to right in PEMDAS.  Same with addition and subtraction.  Here's the first link from Google (doing a search on pemdas) which says the same.

[https://www.mathnasium.com/eagan/news/what-pemdas-e](https://www.mathnasium.com/eagan/news/what-pemdas-e)

---

### Post by lucant on 2023-04-08
[QUOTE=jonfisher;14138136]My friend says the following about this observation:


The full analysis of this situation is now clear: it depends on whether you think like a programmer or like a mathematician. C, and, through its influence over the decades, apparently many other languages as well -- clearly including Perl, as shown here -- is documented and expressive as evaluating expressions from left to right, except for performing parentheses first expression evaluation and bottom to top (or deepest first). This is just a different rule than what a mathematician or teacher would consider the proper rules of arithmetic, i.e. PEMDAS. Clearly, what's accidentally here is that all of the participants on this trip are programmers, who grow up WTF passengers, doctors who grow up organic, are used to C-rules, and therefore actually consider 36 "the right answer" because that's it that the official rules of the programming language offer. However, I claim that while this is certainly the expected result of calculating in an organizational language, it is nevertheless not the "right answer" that someone who knows how to do arithmetic correctly should get when doing the calculator "with pencil and paper" . Outside the program source code, the PEMDAS rules are in effect and the real-world correct answer is 1. The unfortunate fact, however, is that several generations of programmers have grown up internalizing C-style left-to-right evacuation rules , to the point where they now consistently fail to recognize that exposing this method to the outside, such as on the screen and workings of a calculator application, is a semantic error that muddies the waters and perpetuates and spreads this dangerous misperception.

If you like, you can add that your math whiz friend says there's no room for argument here: these are the facts, and your calculator apps, as they stand today, are only suitable for programmers, not the general public. For the general public, an expression evaluator that specifically implements PEMDAS should be used instead of C-like left-to-right evaluation. I would be happy to try writing said PEMDAS evaluator.

Adding another set of parentheses forces the language to evaluate the entire right side of the division FIRST, forming a denominator of 48 just like in PEMDAS. The effect is, in essence, to force the language/code to operate from M before D, whereas in strict left-to-right order, in the original expression, the interpreter encounters, and therefore executes, D before M.[/QUOTE ]


Sorry, but that's not what the first post in this thread proposed.


There is a clear picture of a calculator with the following expression:
48÷8(14-8)
Which is different from:
8/48 (14-8)
Which would be equal to:
48[8(14-8)]

---

### Post by jonfisher on 2023-04-08
It depends what source you use.  Here multiplication "is of higher precedence than division."

**Mixed division and multiplication**

In some of the academic literature, [multiplication denoted by juxtaposition]("https://en.wikipedia.org/wiki/Multiplication_denoted_by_juxtaposition") (also known as [implied multiplication]("https://en.wikipedia.org/wiki/Implied_multiplication")) is interpreted as having higher precedence than division, so that 1 ÷ 2*n* equals 1 ÷ (2*n*), not (1 ÷ 2)*n*.[SUP][[1]]("https://en.wikipedia.org/wiki/Order_of_operations#cite_note-Bronstein_1987-1")[/SUP] For example, the manuscript submission instructions for the *[Physical Review]("https://en.wikipedia.org/wiki/Physical_Review")* journals state that multiplication is of higher precedence than division,[SUP][[20]]("https://en.wikipedia.org/wiki/Order_of_operations#cite_note-APS_2012-23")[/SUP] and this is also the convention observed in prominent physics textbooks such as the *[Course of Theoretical Physics]("https://en.wikipedia.org/wiki/Course_of_Theoretical_Physics")* by [Landau]("https://en.wikipedia.org/wiki/Lev_Landau") and [Lifshitz]("https://en.wikipedia.org/wiki/Evgeny_Lifshitz") and the *[Feynman Lectures on Physics]("https://en.wikipedia.org/wiki/Feynman_Lectures_on_Physics")*.[SUP][URL="https://en.wikipedia.org/wiki/Order_of_operations#cite_note-NB1-24"][d]

Source:[/URL][URL="https://en.wikipedia.org/wiki/Order_of_operations"]https://en.wikipedia.org/wiki/Order_of_operations

[U]
Using this logic, then the answer would be 1 as multiplication is done first

Sorry, I couldn't UN - UNDERLINE that stuff above


Regardless, things need to be standardized before a rocket explodes on lift off
[/U][/URL]
[/SUP]

---

### Post by sirxetwnk on 2023-04-08
Hello all.  I'm **kernelhead**'s "friend who is a genius at math," and I came here to participate directly and "cut out the middleman."

I am both a math nerd *and *a programmer of 40+ years' experience.  I remember everything from every math or computer course I've ever taken, from the 1st grade in 1969 to grad school in the mid-to-late 2000s, and I continue to learn new things online almost every day.  So, while I'm virtually certain of everything I'm going to say, I also leave room for the possibility, however slim I may consider it to be, that *maybe, **just maybe, *something fundamental has changed in the last fifty years -- but the basics of arithmetic seem to me to be something that *shouldn't *change,* shouldn't *evolve over time -- they should remain rock solid forever.  Otherwise the  whole edifice of mathematics collapses.

So, now on to the matter at hand: the evaluation of the expression **48/8*(14-8)**, specifically as to "what's the *right answer*?"  Some people insist it's **36**, while others insist it's **1**.  One fellow says it's ambiguous because the answer can be changed by adding another set of parentheses, *viz: ***48/(8*(14-8)**.  Someone even dismisses it as a joke.  But it's definitely not a joke: the Internet is full of confusion about it; there are actual physical pocket calculators some of which give one answer and some the other; and I consider it vitally important to at least *try *to get everybody "back on the same page again," as they were before pocket electronic calculators, let alone computers, came onto the consumer market in the mid-1970s.

Prior to calculators and computers, there was no argument: the rules some of us (or at least our children) were taught as PEMDAS or some such acronym, were the one-and-only standard, whether they were *actually called* PEMDAS or not: everybody was taught that you evaluate parenthesized expressions first, then exponential expressions, then multiplication, then division, then addition, and finally subtraction.  (Some people in this very thread have another name for it, which uses the term "brackets" instead of "parentheses," and they seem to omit the notion of exponentials altogether, but it's still the same rules.)  By those standards, which had been established over literally hundreds of years, the expression under discussion evaluates thusly:

P: **(14-8) = 6**, and the expression becomes **48/8*6**
E: there are no exponentials, so the expression doesn't change
M: **8*6 = 48**, and the expression becomes **48/48**
D: **48/48 = 1**

and we're done.  That answer, **1**, is, was, and ever shall be, the *right *answer, according to hundreds of years of mathematics and mathematicians and the rules of PEMDAS.

When **kernelhead **first showed me his screenshot of the Ubuntu calculator delivering the value **36 **for this expression, I was horrified.  It was clear where it came from -- naive left-to-right evaluation respecting only the Parentheses part of operator precedence rules:

P: **(14-8) = 6**, and the expression becomes **48/8*6**

Then, [I]as though pressing one key at a time on a 1970s calculator, 

[/I]**4**    - display would show **4**
**8 **   - display would show **48**
**/**     - display would show **48**
**8**    - display would show **8**
*****    - display would show **6** because calculator performs **48/8** immediately
**6**    - display would show **6** 
**=**   - display shows **36**

Which is fine, *as long as you recognize that by pressing the keys in that order you've naively performed the operations in the wrong order,* which is to say you've calculated the expression** (48/8)*(14-8)**, a.k.a. **(48/8)*6**, *instead of what you were given*.  If you've evaluated the *wrong expression, *you cannot have done otherwise than to obtain the [I]wrong answer!

[/I]To get the right answer on a naive left-to-right calculator, *you, the human being, had to know* the rules of arithmetic and realize that the original expression requires *a different order of button-pressing:*

**4**  - display shows **4**
**8 ** - display shows **48**
**/**  - display shows **48**
**(**  - (display might show various things depending on calculator, but probably still **48**)
**8**  - display shows **8**
*****  - display shows **8**
**(**  - (display probably still shows **8**)
**1**  - display shows **1**
**4**  - display shows **14**
**-**  - display shows **14**
**8**  - display shows **8**
**)**  - calculator evaluates inner parenthetical expression **14-8**, so display shows **6**
**)**  - calculator evaluates outer parenthetical expression **8*6**, so display shows **48**
**=** - calculator finally performs the division entered before the first parenthesis, so, **48/48**; display shows **1**

Worse, for a good many years in the beginning, calculators *didn't have *parentheses.  If an expression had parentheses, you had to do the part in parentheses first, *write down the answer*, and use that in a whole separate, second (or third, or...) calculation to get the final answer:

**1** - display shows [B]1
[/B]**4** - display shows **14**
**-**  - display shows **14**
**8** - display shows **8**
**=** - calculator computes **14 - 8**, so display shows **6**, and you *write it down.*

**8** - display shows **8**
***** - display shows **8**
**6** - display shows **6**
**=** - calculator computes **8 * 6**, so display shows **48**, and you *write it down.* 

At this point it's clear that the final calculation **48/48**, which I hope most of you don't need a calculator to perform, but just for the sake of completeness:

**4**  - display shows **4**
**8**  - display shows **48**
**/**  - display shows **48**
**4**  - display shows **4**
**8**  - display shows **48**
**=**  - calculator computes **48 / 48**, so display shows **1**, and [I]this is the final, and correct, answer.

[/I]Don't take my word for it; you should be able to Google up any number of 1970s calculator owner's manuals, which often went into lengthy explanations of just how to do these sorts of calculations correctly.

(As a math nerd, I myself had HP calculators, which used a whole other notation that required even more mental agility and mental rearrangement of terms: Reverse Polish Notation (RPN).  Other kids would ask to borrow my calculator, I'd hand it to them, and after about ten seconds they'd hand it back because they *couldn't find the = key,* because there *wasn't* one.  See, an expresson like **3 + 4** is written in what is known as "infix" notation: the operator comes *between *the operands (things to be operated upon).  But other notations exist: *prefix *notation, in which the same expression is written as **+ 3 4 **, and *postfix *notation, in which it is written as **3 4 +**.  On HP's RPN calculators, instead of an **= **key, there was an **Enter** key, which you pressed in order to "push" the displayed entry onto a stack; the arithmetic operations then popped their operands off the stack, operated on them, and left the result on the top of the stack.  On the HP, the calculation we're considering here today would look like this:

**4**        - display shows **4**; don't care about rest of stack
**8**        - display shows **48**; don't care about rest of stack 
**Enter ** - display shows **48**; a *copy* of the value **4****8** is pushed onto the stack
**8**        - display shows **8**; value **48 **is still on the stack, but invisible 
**Enter**  - display shows **8**; a *copy *of the value **8 **is pushed onto the stack, ahead of the **48 **already there
**1**        - display shows **1**; values **8 **and **48 **are still on the stack 
**4**        - display shows **14**; values **8 **and **48** are still on the stack
**Enter**  - display shows **14;** a *copy *of the value **14 **is pushed onto the stack, ahead of the **8** and **48 **already there
**8**        - display shows **8**; values **14**, **8**, and **48 **are still on the stack
**-**        -  subtracts **8** (on the display) from **14** (first thing on the stack), placing **6** in the display, removing **14 **fackrom the stack,leaving **8** and **48** still on the stack
*****        - multiplies **6** (on the display) with **8** (first thing on the  stack), placing **48 **in the display, removing **8** from the stack, leaving** 48 **still on the stack
**/**        - divides **48 **(on the display) into **48 **(first thing on the stack), placing **1 **in the display, removing **48** from the stack, leaving it empty

Again, the *right answer *is **1**.

Incidentally, this is also exactly how the programming language Forth, and the page-description language PostScript, operate.

But I digress.)

The problem with the Ubuntu calculator and many others isn't precisely that it "gives the wrong answer," but rather that it gives an answer that *computer programmers *have *come to think of *as right, when it is actually *only *"right" *for *computer programmers *while they are actually programming.*  That's because programmers have spent the last 30 years working either in C, or in a language whose syntactic roots lie in the C tradition -- and the C Language Standard decreed, over thirty years ago, that expression evaluation *in a C source statement *would proceed strictly left-to-right, except for performing parenthesized expressions first (by recursively applying the same rules).  Under that standard, a program statement such as
[B]
x = 48/8*(14-8)
[/B]
*will, should and does *deliver the result **36**.  

The problem is that people confuse this *result*, which is indeed "in accordance with the rules of the programming language" with "the *right answer,*" *mathematically, *which is a whole other thing.  That's perfectly okay as long as it remains buried in a program that the user never sees in that form, and the calculations do what they're supposed to do.  The problem here today, though, is that this discrepancy has now been exposed to the user and promoted as the "right answer," which is absolutely untrue anywhere other than during the actual act of computer programming, and that the confusion -- including adamant *defense *of the wrong answer as right! -- represents a disaster waiting to happen.  We've raised, now, a generation or two of people out there (and in here today!) who *don't even know they're wrong*.  If you believe **36 **to be the right answer here today, you've made the very mistake our teachers warned us about, of "trusting the calculator," which in this case translates into "treating all arithmetic expressions as C or C-like source code" and calling that result "the right answer," which it isn't, anywhere other than in a line of program source code.  I wouldn't want to have a tax accountant who did arithmetic your way, or used a calculator, or calculator app, that did it your way!  Jeez, imagine the uproar.  I won't be surprised to see this problem lead to tragedy someday, as this particular bit of ignorance and misconception gradually spreads through the engineering professions and starts to produce fatal errors in the designs of bridges, buildings, vehicles, spacecraft, etc.  (I will try hard to get onto the Congressional committee investigating the disaster, so that the right one of you gets the blame.)

So, please, *please, I **beg **you, *programmers, please do everything in your power to disseminate *clarity *rather than *obfuscation*: at the very least, put a glaring, obnoxious, text banner in your calculator display, warning the user that "this app evaluates arithmetic expressions according to the rules of [language it's written in], *not *by the PEMDAS rules of proper arithmetic!"  Better yet, instead of just letting your language interpret raw user input, I strongly urge you to implement (or find; I expect someone has already written) a proper PEMDAS-observing expression evaluator, that you put the user's input through in order to just plain give them the answer that is right *in the everyday world, not just yours.  ***Please.***&#8203;*

---

### Post by coffeecat on 2023-04-08
> **sirxetwnk said:**
> 
So, please, *please, I **beg **you, *programmers, please do everything in your power 

This is a volunteer end-user forum, whose purpose is *"...to provide support for Ubuntu."* (From the forum [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules").) To be clear: we all, including forum staff, are ordinary users, and not employed by Canonical. There are no developers here. Any diatribe directed at app developers is out of place here.

---

### Post by lucant on 2023-04-08
Interesting, so it goes like this:
48÷8(14-8)
48÷8x6
48÷48=1

---

### Post by donald187 on 2023-04-08
The following two math professors say that the expression is ambiguous.

By George Mark Bergman,

 who received his Ph.D. from Harvard and was a professor at the University of California at Berkeley.

[https://math.berkeley.edu/~gbergman/misc/numbers/ord_ops.html](https://math.berkeley.edu/~gbergman/misc/numbers/ord_ops.html)

and by John Baez of UC Riverside (who mentions physics).

[https://math.ucr.edu/home/baez/physics/General/binaryOps.html](https://math.ucr.edu/home/baez/physics/General/binaryOps.html)


Credits:
[URL="https://en.wikipedia.org/wiki/George_Bergman"]https://en.wikipedia.org/wiki/George_Bergman
[/URL][https://mathdept.ucr.edu/john-baez-ams](https://mathdept.ucr.edu/john-baez-ams)[URL="https://en.wikipedia.org/wiki/George_Bergman"]
[/URL]

---

### Post by sirxetwnk on 2023-04-08
> [COLOR=#000000][I][IMG]https://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **sirxetwnk** [[IMG]https://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("https://ubuntuforums.org/showthread.php?p=14138152#post14138152")
So, please, *please, I **beg **you, *programmers, please do everything in your power

[/I]
[/COLOR]
[COLOR=#000000]This is a volunteer end-user forum, whose purpose is [/COLOR]*"...to provide support for Ubuntu." (From the forum [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules").) To be clear: we all, including forum staff, are ordinary users, and not employed by Canonical. There are no developers here. Any diatribe directed at app developers is out of place here.*

First, I apologize; I am here for the first time ever; I don't even run Ubuntu, myself -- was about to switch to it, when it suddenly broke my heart by "going adware" a few years back.  Please tell me if that's been backed out.

Second, I apologize; I didn't mean to deliver a "diatribe;" but I'm alarmed.  If I could, I'd post this *everywhere*, including on the national news broadcasts every night.  Make it part of the national conversation, get a mathematician elected President, appoint a few of 'em to the Supreme Court, and get PEMDAS enshrined in the Constitution, if that's what it takes to hammer ignorance and error out of existence.  I'm semi-joking, of course, but *only semi!*

Third, I apologize for inappropriately addressing "developers" in this forum.  I assumed that anybody who thinks C expression-evaluation syntax produces "the right answer" *must *be a programmer, because they're *thinking* like programmers -- and that was the least insulting, most-legitimate, excuse I could think of for their believing **36** was "the right answer" to the evaluation of today's expression.  Hence I addressed this readership as "developers."  Feel free to tell me what label you'd prefer, and I'll happily edit that sentence.  Or should I just go for the gold, turn off my inner "filter," and say flat out, *"Anybody here, or elsewhere in the Universe, who thinks **36** is the right answer, is **WRONG** and needs to correct their thinking or stop participating in computing." * That feels like it might be rude, so I'd prefer *not *to say that.  Please advise.

---

### Post by Dennis N on 2023-04-08
I have been teaching algebra for years. Algebra textbooks deal with this issue usually in the beginning.

From _Elementary Algebra_ by Harold R. Jacobs, page 40:

> The fact that the answer to a problem that requires several operations (and without grouping symbols) can depend on the order in which they are done has led mathematicians to make rules for dealing with such problems. The rules are:

First, figure out the powers if there are any.
Then do the multiplications and divisions in order the appear from left to right.
Finally, do additions and subractions in order they appear from left to right

You are right that in the absence of rules, your expression is ambiguous. Applying the long accepted rules above, the value of the expression is not ambiguous. If you want to get it right on a math test, use the rules.

---

### Post by donald187 on 2023-04-08
Interesting and clear exposition of the problem.  Basically the difference is whether you believe a(b) = a x b or if you believe a(b) = (ab).  The difference is 36 and 1.

[https://plus.maths.org/content/pemdas-paradox](https://plus.maths.org/content/pemdas-paradox)

---

### Post by TheFu on 2023-04-08
> **sirxetwnk said:**
>  
So, please, *please, I **beg **you, *programmers, please do everything in your power to disseminate *clarity *rather than *obfuscation*: at the very least, put a glaring, obnoxious, text banner in your calculator display, warning the user that "this app evaluates arithmetic expressions according to the rules of [language it's written in], *not *by the PEMDAS rules of proper arithmetic!" 

The first bug I found in production code at my first real job (real-time GN&C software) was because of this problem.  The Programmers Guide for the language was clear and even had a warning. I was completely new to the language (I'm certain nobody here has heard of that language), so I wasn't assuming anything.  The code I was reviewing had already been sent to the customer for their review with the bugs.  The guy who wrote it had been in that job over 10 yrs and the other 3 experienced people who reviewed it failed to see the problem.

Bad software has a way of making otherwise excellent programmers humble.  Given enough time, every great programmer will make a bonehead mistake.

---

### Post by donald187 on 2023-04-08
> **Dennis N said:**
> I have been teaching algebra for years. Algebra textbooks deal with this issue usually in the beginning.

From _Elementary Algebra_ by Harold R. Jacobs, page 40:



You are right that in the absence of rules, your expression is ambiguous. Applying the long accepted rules above, the value of the expression is not ambiguous. If you want to get it right on a math test, use the rules.

My mistake.  I shouldn't have said "ambiguous".  There are apparently two camps that believe different rules.  I was brought up with your rules.

---

### Post by lucant on 2023-04-08
I'm going to say why I believe the answer is 36.
48÷8(14-8)
1st I will solve what is between parentheses 14-8=6
2ºI will multiply the result by what? Why 48? Why 8? I will NOT multiply by the result of division, i.e. 48÷8=6
3ºOnly then will I multiply... 6x6=36

---

### Post by donald187 on 2023-04-08
> **donald187 said:**
> My mistake.  I shouldn't have said "ambiguous".  There are apparently two camps that believe different rules.  I was brought up with your rules.

Actually, the first professor I linked to did use the term "ambiguous" because he says there is not broad agreement on the rules.

---

### Post by oldfred on 2023-04-08
[https://leachlegacy.ece.gatech.edu/revpol/](https://leachlegacy.ece.gatech.edu/revpol/)

This is how I would enter it.

48/8(14-8)

48 enter 8 / enter 14 enter 8 - * = 36

I have issues understanding standard calculators as I have used HP's RPN from the beginning.

---

### Post by donald187 on 2023-04-09
> **donald187 said:**
> Interesting and clear exposition of the problem.  Basically the difference is whether you believe a(b) = a x b or if you believe a(b) = (ab).  The difference is 36 and 1.

[https://plus.maths.org/content/pemdas-paradox](https://plus.maths.org/content/pemdas-paradox)

Apparently there are two sets of rules.  One where 48 ÷ 8(6) = 48 ÷ 8 x 6 = 6 x 6 = 36 and one where 48 ÷ 8(6) = 48 ÷ (8 x 6) = 48 ÷ 48 =1. The first one being Dennis N's PEMDAS and  the second one being jonfisher's multiplication by juxtaposition.

---

### Post by The Cog on 2023-04-09
Ooh! This has bifurcated into two different precedence arguments:

Firstly, the claim that 48/8(14-8) is ambiguous.
Does it mean 48/8*(14-8) or 48/(8*(14-8))? i.e. Is juxtaposing two values without an operation symbol just a multiplication operation, or does it have higher precedence than other multiplications? I.e. is there an implicit parenthesis round that implicit multiplication?
I was taught (admittedly a long time ago) that juxtaposition just meant multiplication, and that parenthesis was sometimes needed to raise precedence.
The existence of this thread proves to me that the juxtaposition is (in this instance) ambiguous though, because different folk are arriving at different answers, and best practice would be to avoid ambiguous juxtapositions.

Secondly, from sirxetwnk (quoting PEMDAS):
Does multiplication have a higher precedence than division?
> P: (14-8) = 6, and the expression becomes 48/8*6
E: there are no exponentials, so the expression doesn't change
M: 8*6 = 48, and the expression becomes 48/48
D: 48/48 = 1
I was taught that multiplication and division were equal precedence and should be evaluated left-to-right. i.e. 1/2*3 = 1.5, not 1/2*3 = 0.166.
So I disagree with sirxetwnk here. I think PEMDAS should really be PE(MD)(AS). 
Actually, if multiplication has a higher precedence than division, then the first argument becomes moot because juxtaposition then has a higher precedence than division and there is no ambiguity in the original string.

---

### Post by mIk3_08 on 2023-04-09
lol... I think I might need more studies around here. What the heck are thinking.
Why are you doing that if you want an answer of "1". I'm not good in math but, is this a joke?

---

### Post by maglin2 on 2023-04-09
My Maths teacher advised us that if there was ambiguity in an expression we presented that could be resolved by parentheses he would mark it wrong, even if we'd numerically evaluated it to the correct solution. The value in abstraction came from application.

---

### Post by Topsiho on 2023-04-09
I think that the only answer is that there ===> is no answer <=== here, as the expression contains an** implicit multiplication** which is not in PEMDAS, which is mentioned somewhere above and which should be adhered to ( but often is not) by algebraic calculators.
Human calculators using RPN should notice this implicit multiplication, and be alerted, but users of algebraic calculators, in which they put an expression and then just hit the = - key, might never know the error or it's cause.
That's why technicians and mathematicians should use RPN: the errors they make, they make themselves :)

I know examples that algebraic calculators of the same manufacturer get different answers for the same expressions, containing implicit multiplications.

The P in PEMDAS which means Parentheses, at first made me hesitate, but it's the** illegal** (as it is not in PEMDAS) leaving out of a multiplication sign that is the culprit.

For all sorts of operations that are not in PEMDAS manufacturers of algebraic calculators have to invent themselves how to handle these and they often do this differently, so you should study the manual well. 

Topsiho

---

### Post by #&amp;thj^% on 2023-04-09
> **oldfred said:**
> 
I have issues understanding standard calculators as I have used HP's RPN from the beginning.
Same here, and *my* preferred choice.

---

### Post by jonfisher on 2023-04-09
I emailed someone that was a professor of math at Baylor University & he said the answer is 1.
I emailed an engineer who told me the answer is 36.

Draw your own conclusions.

---

### Post by Topsiho on 2023-04-09
I'm afraid I put my answer (#40) in the wrong place, so please have a look there.
I argued that there is no answer, as implicit multiplications are not in PEMDAS and so are treated differently, if at all, in different calculators, even from  the same manufacturer.
Though PEMDAS is followed by most modern manufacturers of algebraic calculators (the usual calculators, sigh), anything outside PEMDAS is implemented differently. And so is implicit multiplication. The leaving out of the multiplication sign might mean that the multiplication  has a higher priority, or it might mean nothing. Which here makes all the difference.

That means that for serious use only RPN is advisable. So any student of Math, Physics, Astronomy or a technical study shoulld use only RPN. Unfortunately there are not so many of these nowadays.

In this age of powerful laptops maybe calculators are obsolete, and are replaced by programming languages and math or cad tools.
The first thing to do is study their priority rules, to prevent unpleasant surprises.

The best RPN calculator I know is Free42, that you can install in Ubuntu, PLease use the decimal version (which is quite another topic!)
This calculator mimics the quite legacy HP42 RPN calculator, where the newer ones have a very sophisticated programming language.

Topsiho

---

### Post by jonfisher on 2023-04-09
Concerning HP calculators, my friend posted about them here.

Just now he told me this:

HP calculators with RPN are just like any other kind: you have to know what you're doing, and push the buttons in the right order, to get the right answer.  I gave the exact HP RPN procedure for yesterday's equation, in one of my forum posts.   Now, if HP has since produced a line of calculators that don't use RPN, and that perhaps show the whole expression on the display, and that evaluate it like C, I haven't heard about it.
Don't problem is that it used to be common knowledge that just pressing the buttons on the calculator in the order of the symbols appeared on a line of paper (or, worse today, a line of screen text) would not give you the right answer, particularly if parentheses, division,  and/or any kind of ambiguity, were involved. You absolutely had to understand PEMDAS, be able to recognize and account for ambiguities , choose the correct interpretation thereof, and alter the order of your button pressing, to get the right answer.  THAT is what's been lost.

The whole* problem ^^^

---

### Post by jonfisher on 2023-04-09
[B]Speaking of History

"Multiplication and division[/B]

 If the &#8220;rules&#8221; evolved gradually through usage, it should not be surprising that some are still not fully settled:

 3. Some of the specific rules were not yet established in Cajori's own time (the 1920s). He points out that there was **disagreement as to whether multiplication should have precedence over division**, or whether they should be treated equally. The general rule was that parentheses should be used to clarify one's meaning - which is still a very good rule. I have not yet found any twentieth-century declarations that resolved these issues, so I do not know how they were resolved. You can see this in "Earliest Uses of Symbols of Operation" at:

   [URL="http://jeff560.tripod.com/operation.html"]http://jeff560.tripod.com/operation.html"

source: [/URL][https://www.themathdoctors.org/order-of-operations-historical-caveats/](https://www.themathdoctors.org/order-of-operations-historical-caveats/)

---

### Post by Topsiho on 2023-04-09
Yes, indeed. That's correct.

Using an RPN calculator only thing you need to know is PEMDAS, or **knowledge of the priority rules the author uses**, which you should follow also. You need not know the priority rules of your RPN calculator, as you are the processor yourself!
This answers also a post above in which a journal forces you to follow some rules apart from PEMDAS. In RPN you then just do that, everyone happy. PEMDAS is not the holy grail, but is a set of rules that are commonly agreed to.

That is lost using something else than RPN, unfortunately.

Edit: I answered here jonfisher's previous post

Topsiho

---

### Post by chris0nlinux on 2023-04-09
Hello,):P

I have been thinking about this for hours. I e-mailed my former Mathematics teacher and she insists it is 36, as (14-8) should be resolved first.
Every calculator I have tried finds it is 36. I think gnome-calculator is correct

---

### Post by jonfisher on 2023-04-09
> **chris0nlinux said:**
> Hello,):P

I have been thinking about this for hours. I e-mailed my former Mathematics teacher and she insists it is 36, as (14-8) should be resolved first.
Every calculator I have tried finds it is 36. I think gnome-calculator is correct


Yep, and a retired math professor I emailed said the answer is 1.

I think we will just have to conclude that this is ambiguous.  Which is unfortunate.  I just hope everyone at Nasa uses extra parenthesis when sending those people to the moon again!  Smiles !

---

### Post by mIk3_08 on 2023-04-09
I prefer not to use calculator when you have to use some reasoning. Its just like, Which comes first?.. The egg or the chicken.? HELLO!...
Regards and cheers.

---

### Post by QIII on 2023-04-09
It's not at all ambiguous.  The answer is clearly and unequivocally 1.

Consider the following:

8(fn(x))
8*(fn(x))
(8(fn(x))
(8*(fn(x)) 

Then consider this:

Is 8x neither acceptable nor conventional notation because it does not include x (the multiplication symbol "x") or *?  If so, then generations of mathematicians have been wrong, while late 20th Century developers creating computer languages have set them straight. No, that's simply not the case. 
 Developers have to disambiguate something that is not ambiguous except for a misconception perpetuated by computer languages.

How about this ...

x = fn(y)
z = 8x  *(which is to say 8(fn(y))*
q = z
r = z/7

Pick any fn(y).  It could be an ugly, complex function.  You can still solve for r in terms of fn(y) without even knowing or caring what fn(y) is!

Should E = mc^2 be written E = m*c^2?.  I'm going to go against the convention regarding the order of precedents of exponents, and rewrite that as a constant multiplied by a variable for demonstration: E = c^2m.  c is a constant, that is the same pattern as z = 8x, and, going back, the equivalent of 8(fn(y)).  And the expression 8(fn(y)) is the exact thing you are arguing about and for which you get different answers:  One categorically incorrect but accepted as the correct answer by many, the other -- the correct one -- thought incorrect.

Sorry.  I spent eight years studying Mathematics at a couple of Universities.  I went on to own a software development company.  8x is conventional.  8*x is quite correct, but the convention is 8x.

The answer is 1, and there is no ambiguity about it.

Yours truly,

A guy with a whole lot of ambiguous letters after his name.

---

### Post by Topsiho on 2023-04-10
I am  sorry that apparently not everyone, even Math teachers (I was one myself) understands that priorities of operations are only something that are agreed upon. One of the agreements, used in the USA (where most calculators are built) and in Japan, and some other countries, is PEMDAS. Parentheses first, then Exponentiation, then Multiplication and Division, and after that Addition and Subtraction. M and D, and A and S have equal priority, and are done from left to right.  When applying these rules the expressions should be divided first into subexpressions if necessary.
As most, if not every "normal  ?" calculators are built in the USA or Japan, they should obey PEMDAS.
Ambiguity arises when an operation is not in PEMDAS. Then a manufacturer has to decide for himself what priority he is going to program when necessary. Such as implicit multiplication, which in some calculators has a higher priority then a normal multiplication. That should be mentioned in the manual, and the user should be aware of that. And the author of the expression!

E.g.: what is -4² ?  Is it 16 or is it -16. Is this (-4)²  or is it -(4²) ? It is not in PEMDAS and so it is not defined if you don't know the priority rules that the author used. Try this on your calculator and remember the result.

How it is done in some examples is not an indication, as the priority rules in these examples are not known, and may vary from country to country, from one profession to another, and so on.

Here in Holland until recently (end 20thh century) square roots were not considered  exponents an had a _lower_ priority than Multiplication and Diviision. For historic reasons, not mathematical.

The very, even decisive, strong point of RPN is that there is not a preprogrammed set of priorities, which you should know and follow.

Howgh,

Topsiho

---

### Post by maglin2 on 2023-04-10
Instinctively:
I think 48÷8y where y is 6 = 1.
Whereas:
I think 48÷8×y where y is 6 = 36.
So I accept the multiplication operator implicit in 8y as taking precedence over left right working. Or perhaps I treat 8y as (8×y).
Not really pondered this much before this thread came up.

---

### Post by QIII on 2023-04-10
This all comes down to a convention that is well known to all of us from the 60s, actuaries, old slide-rule users, actuaries and those who don't want their orbital spacecraft to crash on the planet rather than entering orbit.

With the advent of the digital computer, Discrete Mathematics rose to the forefront.  Unfortunately this caused the loss of the memory of an important convention because Discrete Math is not the end-all, to wit: that if fn(x) = (14-8), then 8(fn(x)) is not equivalent to 8*(14-8).  There is still a vestige of that memory in the fact that none of you would bat an eye if you encountered 8x with no multiplication operator.  And if I told you beforehand that x = (14 - 8), you would have no problem understanding that 8x = 48.  Then, if I asked you the value of 48/8x,  you would say, cheerfly, "Why one, of course!"  That is because you understand that 8x is a complete element of the expression and you don't hesitate. 

But you would likely correctly draw a different conclusion from 8*(14 - 8)

The lack of the multiplication operator is, or was, a very important convention.  It's not "missing".  It was not included purposefully -- when written out.  Thus, a programmer needs to add parentheses, which should not have been needed, to clarify.

---

### Post by Topsiho on 2023-04-11
It is not important what we think or not, or feel, what it's all about is that the author of an expression wants to tell us what we should put into a calculator (algebraic) or what we should do (RPN) to evaluate that expression so to get the desired result.

The set of priorities of the various operations that he uses must be the same for both him/her and the reader.

It helps to use a standard set, such as PEMDAS, but outside PEMDAS algebraic calculators differ enormously.

If you don't believe that, I invite you to see the manuals of different algebraic calculators. They SHOULD have somewhere, even if hidden, a list of the priorities in that particular calculator. These are different, even if from the same manufacturers. I have two TI's that give different results for some very simple expressions.

We don't know what calculator the author has in mind. We must hope that it obeys PEMDAS, but even that hope is 
smashed if the author doesn't know PEMDAS, as in many countries PEMDAS possibly is replaced with something else, such as only from left to right or something else.
Even in my country (the Netherlands) the priorities were replaced by PEMDAS only recently (end 20th century).

If you write an expression yourself that is to be used internationally, please be sure to use enough parentheses, even if this makes the expression horrible.

If even presumably competent Math teachers don't agree on the results of even such a simple expression as discussed here, then there surely something is wrong!

Topsiiho

---

### Post by donald187 on 2023-04-11
Here's what someone (Gerry Myerson) with a lot of badges and reputation said on math.stackexchange.com.  It was a very popular answer.

> 
There is no Supreme Court for mathematical notation; there were no  commandments handed down on Sinai concerning operational precedence; all  there is, is convention, and different people are free to adhere to  different conventions. Wise people will stick in enough parentheses to  make it impossible for anyone to mistake the meaning. If they mean, [FONT=MathJax_Main]([/FONT][FONT=MathJax_Main]48[/FONT][FONT=MathJax_Main]÷[/FONT][FONT=MathJax_Main]2[/FONT][FONT=MathJax_Main])[/FONT][FONT=MathJax_Main]([/FONT][FONT=MathJax_Main]9[/FONT][FONT=MathJax_Main]+[/FONT][FONT=MathJax_Main]3[/FONT][FONT=MathJax_Main])[/FONT], they'll write it that way; if they mean [FONT=MathJax_Main]48[/FONT][FONT=MathJax_Main]÷[/FONT][FONT=MathJax_Size1]([/FONT][FONT=MathJax_Main]2[/FONT][FONT=MathJax_Main]([/FONT][FONT=MathJax_Main]9[/FONT][FONT=MathJax_Main]+[/FONT][FONT=MathJax_Main]3[/FONT][FONT=MathJax_Main])[/FONT][FONT=MathJax_Size1])[/FONT], they'll write it that way.


[https://math.stackexchange.com/questions/33215/what-is-48-div293](https://math.stackexchange.com/questions/33215/what-is-48-div293)

Biography:

[https://www.mathgenealogy.org/id.php?id=7263](https://www.mathgenealogy.org/id.php?id=7263)

[https://biography.omicsonline.org/australia/macquarie-university/gerry-myerson-408023](https://biography.omicsonline.org/australia/macquarie-university/gerry-myerson-408023)

---

### Post by minidus on 2023-04-11
> **monkeybrain20122 said:**
> It is not really the calculator's fault but the ambiguous way the question is stated, it could mean 
48 /(8*(14-8)) = 1

or 

(48/8)*(14-8) = 36

depends on where you place the brackets. 

In the jargon of the logician the question is stated in a string that is not well formed (and one reason why the notation ".|." for division is rarely used in advanced mathematics)

**^This**

The question was simply not detailed enough for the calculator to read it as *48/(8*(14-8))*. Since nothing else was specified (since no **brackets** specified otherwise) it presumed the division and multiplication were to be executed in the order typed, first solving *48/8*(=6) before multiplying by *(14-8)*(6*6=36).

Multiplication and division have the same priority, so unless brackets specify otherwise a calculator will (or at least should) always solve them in the order typed.

---

### Post by jonfisher on 2023-04-12
If one reads through the entire thread they'll realize that it's simply an ambiguous math problem.   However, I'd like to add the following:

The first online scientific calculator that I type 20/10x2 into gives an answer of 1.
Which shows it's not going left to right and is indeed holding multiplication at a higher precedence than division.
That calculator is at:  [https://www.desmos.com/scientific](https://www.desmos.com/scientific)

There are other online sci. calculators that also give the answer of 1.  And there are others that don't.

The 2nd online calculator I googled also gives an answer of 1 at [https://www.geogebra.org/scientific](https://www.geogebra.org/scientific)

---

### Post by sudodus on 2023-04-12
> **minidus said:**
> 
[QUOTE=monkeybrain20122;14138060]It is not really the calculator's fault but the ambiguous way the question is stated, it could mean 
48 /(8*(14-8)) = 1

or 

(48/8)*(14-8) = 36

depends on where you place the brackets. 

In the jargon of the logician the question is stated in a string that is not well formed (and one reason why the notation ".|." for division is rarely used in advanced mathematics)
**^This**

The question was simply not detailed enough for the calculator to read it as *48/(8*(14-8))*. Since nothing else was specified (since no **brackets** specified otherwise) it presumed the division and multiplication were to be executed in the order typed, first solving *48/8*(=6) before multiplying by *(14-8)*(6*6=36).

Multiplication and division have the same priority, so unless brackets specify otherwise a calculator will (or at least should) always solve them in the order typed.[/QUOTE]

Compare also **[FONT=Courier New]bc[/FONT]** and **[FONT=Courier New]bash[/FONT]**:
```

$ bc
bc 1.07.1
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006, 2008, 2012-2017 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
48/8*(14-8)
**36**
48/8(14-8)
(standard_in) 2: syntax error
quit
$ bash -c 'echo $((48/8*(14-8)))'
**36**
$ LANG=C bash -c 'echo $((48/8(14-8)))'
bash: line 1: 48/8(14-8): syntax error in expression (error token is "(14-8)")

```

**[FONT=Courier New]bc[/FONT]** and **[FONT=Courier New]bash[/FONT]** do not  'assume' a multiplication operator, and that behaviour would help in the calculator too.

---

### Post by Topsiho on 2023-04-12
Hello Sudodus,

In your examples you changed the expressions, so they obey the normal PEMDAS rules. And then / and * have the same priority, and are executed from left to right. No problem then.
But omitting * before at bracket changes everything:
This is not in PEMDAS, and should be considered illegal, as it is in (only) one of my calculators. And treated differently in others.
Some interpret this as giving the multiplication (everyone agrees it is a multiplication, only because it usually is) a higher priority, and should be executed first.
One of my calculators even has two rules for different implicit multiplications, which take a considerable time to understand.
It is bad practice to invent rules, or use invented rules that depend on who invented them.

Unfortunately in every algebraic calculator priority rules are used that are invented and implemented, that are not in PEMDAS, and which are not agreed upon by any convention.
.
Even calculators of the same manufacturer differ. See their manuals and just shiver...

Btw,: did you know that Meneer van Dale is obsolete?

Groetjes, Topsiho.

---

### Post by sudodus on 2023-04-12
> **Topsiho said:**
> 

 ... omitting * before at bracket changes everything:
This is not in PEMDAS, and should be considered illegal ...

We agree about that :-)

Edit: Sorry, but I'm an ignorant fool, I never heard of Meneer van Dale.
Edit 2: Seems to be somewhat similar to 'Rappakalja' in my language :-P

---

### Post by Topsiho on 2023-04-12
In Python3:

>>> 48/8*(14-8)
36.0
>>> 48/8(14-8)
<stdin>:1: SyntaxWarning: 'int' object is not callable; perhaps you missed a comma?
Traceback (most recent call last):

Topsiho

---

### Post by Topsiho on 2023-04-12
To sudodus:

Probably you are very young :)
Meneer van Dale was the Dutch version of PEMDAS. In which square roots (**w**orteltrekken) was not considered an exponentiation, and had a **lower** priority then multiplication and division, but higher than adding and subtraction. It was in place for centuries (since Descartes was in Holland) and only replaced by PEMDAS during the nineties, probably because calculators not giving the correct answers.
Meneer van Dale** w**acht op antwoord.
Mister van Dale waits for an answer: M (VD) W (OA) as an obsolete Dutch PE(MD)(AS)

Topsiho

---

### Post by sudodus on 2023-04-12
@Topsiho,

I see now why you mention Meneer van Dale **w**acht [op antwoord} in this thread :-)

Otherwise it seems to be similar to the board game 'Rappakalja' in my language.
Maybe both are inspired by [https://en.wikipedia.org/wiki/Balderdash](https://en.wikipedia.org/wiki/Balderdash)

---

### Post by TheFu on 2023-04-12
I was consistently taught PEMDAS in the 1970s and later. No other order was considered valid.

---

### Post by Topsiho on 2023-04-13
@ sudodus

Thank you for your very friendly reply, that made clear to me that you are not Dutch. I know your alias sudodus for a very long time and for some reason thought you were Dutch, without any doubt.

Sorry for that, and I apologise.

In this thread this kind of unthinking assumption is equivalent to the assumption that a calculator always gives a correct answer. In some cases, different from calculator to  calculator this is NOT so, as for commercial reasons the manufacturers add possibilities that do not comply with arithmetical rules.

The advantage of an RPN calculator is that you yourself are the processor, applying the rules you know, and you also have to THINK while entering the input. THINKING is not bad, it is extremely useful, something any math teacher should insist on.

Very unfortunate that RPN has lost the game but some emulators exist, one of which is now my favourite: FREE42 is a clone of the HP42 calculator (as Linux is of Unix).

Did you know that Python3 and bc can handle very very big/large integers? Just try this, it is amazing.

Greetings from Topsiho

---

### Post by sudodus on 2023-04-13
@Topsiho,

Thanks for *your* friendly reply. No need to apologize; I'm Swedish, but it feels nice that you, who live in Holland thought that I was Dutch too.

I remember the old HPs with inverse Polish notation, Long ago I used model '35' and I think model '42'. I knew that bc can handle large integers, but I am not very familiar with Python. (I also remember the size limits for numbers in FORTRAN and C.)

---

### Post by ActionParsnip on 2023-04-13
Google says it's 36 too.....just saying

---

### Post by The Cog on 2023-04-13
Has anyone asked ChatGPT?

---

### Post by ActionParsnip on 2023-04-13
> **The Cog said:**
> Has anyone asked ChatGPT?

Indeed


To solve this expression, you need to follow the order of operations, which is commonly remembered by the acronym PEMDAS (Parentheses, Exponents, Multiplication and Division, and Addition and Subtraction) or BODMAS (Brackets, Orders, Division and Multiplication, and Addition and Subtraction).


Using PEMDAS, we start with the parentheses:


14 - 8 = 6


Now the expression becomes:


48/8 * 6


Next, we perform the division:


48/8 = 6


Now the expression becomes:


6 * 6


Finally, we perform the multiplication:


6 * 6 = 36


Therefore, 48/8*(14-8) equals 36.

---

### Post by Topsiho on 2023-04-13
I' m sorry, you  invented a multiplication where none is in the expression.
You assume, correctly, that the author wanted a multiplication, but for some reason he decided not to write this..
Now.
Even if the expression doesn't follow PEMDAS, many calculators handle this situation differently: is it a multiplication that has the normal precedence or another. I have a calculator that uses two priorities (both higher than the usual one).
What sort of a mess is that?

ANY expressions with this kind of illegal constructions have no  valid answer.

Google should be ashamed! And TheFu is quite right (or his math teacher!)

Topisiho

---

### Post by lucant on 2023-04-13
> **jonfisher said:**
> If one reads through the entire thread they'll realize that it's simply an ambiguous math problem.   However, I'd like to add the following:

The first online scientific calculator that I type 20/10x2 into gives an answer of 1.

Just to relax...
At least the other expression 20/10x2, Ubuntu's calculator gets it right...
So it's 1x1 for Ubuntu's calculator. rs

---

### Post by coffeecat on 2023-04-14
The New to Ubuntu sub-forum is for technical support for those New to Ubuntu. This discussion, albeit interesting, is about conventions for mathematical expressions, and the potential pitfalls of calculators.

*Thread moved to **The Cafe**.*

---

### Post by jonfisher on 2023-04-14
I have had the following people answer 1 as being the correct answer.

A retired software developer.
A retired professor of mathematics, retired from Baylor University.
My sister, using her sons 4th grade math books as the basis for the rule(s).

One person answered 36 as being the answer, whom is my cousin who is an engineer.

But it seems to me like more people, and perhaps calculators answer 36 (even though the first 2 online Sci. calculators I googled gave 1 as the answer).
 
Then there are the people online that say the equation/problem is an "illegal" or "ambiguous" equation/problem.
 
Regardless, am I alone in thinking this could cause a problem, a big problem, in structures being built, rockets being launched, etc....    (?)   Or do most of us believe such designers are using plenty of parenthesis to erase all doubt  (?)

Addendum:  Examples of such problems have occurred, see the post at:  [https://www.linuxquestions.org/questions/linux-newbie-8/ubuntu%27s-calculator-is-wrong-4175723871/page6.html](https://www.linuxquestions.org/questions/linux-newbie-8/ubuntu%27s-calculator-is-wrong-4175723871/page6.html)

---

### Post by zebra2 on 2023-04-14
I put the function in a Texas Instruments TI89 online calculator and get 36.  In a libre office calc spreadsheet a *  is forced between the 8 and the ( which resolves to 36.  So merrly following left to right procedure where the (14-8) is solved by default the result is 36 since 48/8=6 and 6 * 6=36. But just to make sure I'm going to boot up my Puppy Linux and see what that gets.

---

### Post by zebra2 on 2023-04-14
Incedentally, in the 1980's when I was working on my electronics degree I got an A grade on a light physics test when every one of my answers was wrong.  I asked the instructer why the A grade when all of my answers were wrong.  Answer was,  I had turned in my work with the test and my procedures on every problem was correct and the only thing that was being tested was procedure.  If I had not turned in my work I would have failed the test.  It turns out which I discovered a few days later that my  brand new Texas Instruments TI35 calculator had a wrong constant under the speed of light button. Since that time I have placed  a high level of importance on procedure as already clearly expressed in this thread. We don't get a opportunity to reform the expression to accomadate our desired answer. We have to take the expression as displayed and use the correct procedure to solve it.

---

### Post by zebra2 on 2023-04-15
OK, so I booted my Puppy linux and I get 36 as the answer with gnumeric and galculator both. So I add that result to Libre Office Calc, Ubuntu calculator, and the TI89 calculator which all give 36 as the answer and I say let the dogs have it. The puppy is right.

---

### Post by sudodus on 2023-04-15
FORTRAN and C: the compilers refuse to compile without an arithmetic operator between the '8' and the '('; they do not assume multiplication like many people and calculators do ;-) and they apply PEMDAS like our tools in Linux: bc, bash and python3.

```

$ cat pemdas.f; gfortran -o f-pemdas pemdas.f && ( echo '---------------'; ./f-pemdas )
      program pemdas
      
      implicit none
      integer res

      res=48/8*(14-8)
      write(*,*) res
      end
---------------
          36

$ cat pemdas.c; gcc -o c-pemdas pemdas.c && ( echo '---------------'; ./c-pemdas )
#include <stdio.h>
void main(){
	int res;
	res=48/8*(14-8);
	printf("result = %i\n",res);
}
---------------
result = 36

$ cat ambig.c; gcc -o c-ambig ambig.c && ( echo '---------------'; ./c-ambig )
#include <stdio.h>
void main(){
	int res;
	res=48/8(14-8);
	printf("result = %i\n",res);
}
ambig.c: In function ‘main’:
ambig.c:4:16: error: called object is not a function or function pointer
    4 |         res=48/8(14-8);
      |                ^

$ cat ambig.f; gfortran -o f-ambig ambig.f && ( echo '---------------'; ./f-ambig )
      program ambig
      
      implicit none
      integer res

      res=48/8(14-8)
      write(*,*) res
      end
ambig.f:6:7:

    6 |       res=48/8(14-8)
      |       1
Error: Unclassifiable statement at (1)

$ 

```

See also the attached copy of my conversation with chatGPT. I have been told that if one customer suggests something or complains about something nothing happens, but if 3 customers talk about the same thing (in a local shop/store) ... I guess we need to be more than 3 people and not exact copies of each other in order to modify the response of chatGPT :-P

---

### Post by Topsiho on 2023-04-15
> **zebra2 said:**
> Incedentally, in the 1980's when I was working on my electronics degree I got an A grade on a light physics test when every one of my answers was wrong.  I asked the instructer why the A grade when all of my answers were wrong.  Answer was,  I had turned in my work with the test and my procedures on every problem was correct and the only thing that was being tested was procedure.  If I had not turned in my work I would have failed the test.  It turns out which I discovered a few days later that my  brand new Texas Instruments TI35 calculator had a wrong constant under the speed of light button. Since that time I have placed  a high level of importance on procedure as already clearly expressed in this thread. We don't get a opportunity to reform the expression to accomadate our desired answer. We have to take the expression as displayed and use the correct procedure to solve it.

@zebra2
That math teacher was a soulmate of mine: answers do matter but only for a little bit (except when building a bridge or so, in practice). It is the process you used to get the answer, in a school situation, where errors are welcome if you learn from them.
You were very lucky with such a teacher who did not consider the answers only.
And everyone here who comes with an answer, being 1 or 36, did not read nor understand some of my previous posts: when talking gibberish, the answers you get are gibberish. Such as 1 and 36: the road to these answers was arithmetically incorrect, as in (school)arithmetic implicit multiplications are not defined.
The only correct answer is that the expression doesn't obey the conceded upon mathematical rules.
In some programming languages (C, Python, other) it is clearly defined what extra rules are used for entering expressions, which you should read and apply, being aware that elsewhere (other language/calculator) the results are different.
In a school situation those extra rules are not called for and should be avoided, but usually are not. Most schools even force you to use an algebraic calculator, without them even being aware that all of these use extra rules outside  PEMDAS.
And if you apply the not official rules elsewhere your beautiful bridge might collapse the first, or 100th time, an ant crosses it. If you did not read the instruction manual of your algebraic calculator.

:)

Topsiho

---

### Post by donald187 on 2023-04-15
Here's an interesting point of view.  That the rules are only an attempt to describe what mathematicians have done for a long time.  But in fact are not the best possible description of how expressions are evaluated in practice.

[https://www.themathdoctors.org/order-of-operations-historical-caveats/](https://www.themathdoctors.org/order-of-operations-historical-caveats/)

Basically 5 ÷ xy is read more naturally as 5 ÷ (xy) because xy looks like a unit.

(I'd have quoted the first couple of paragraphs but it comes across as one long sentence.)

---

### Post by Topsiho on 2023-04-15
> **donald187 said:**
> Here's an interesting point of view.  That the rules are only an attempt to describe what mathematicians have done for a long time.  But in fact are not the best possible description of how expressions are evaluated in practice.

Basically 5 ÷ xy is read more naturally as 5 ÷ (xy) because xy looks like a unit.



Expressions as we see them today are only a very recent invention. In fact, they are a very concise way of describing a problem to solve. Modern mathematicians are not capable of solving problems as described before let's say the 1700's. Long winded and in a way that the mathematicians of their time could understand, but not those of this time.

It is like a language.
If someone starts speaking another language, he or she might be quite right, but doesn't get across what he/she wants to say.

There is a science that studies math in antiquity, very very much interesting. The Babylonians were extraordinary clever scientists in their time, but only a few scientists now understand their clay tablets.

We have some rules, PEMDAS is not used in all countries, and there are more rules. But if you agree on a set of rules, then you should stick to them, and not follow your instinct or what you think is better. My instinct is using my own language, which I know better and in which I (have learned to) think, but I have to stick here to English. Anders begrijpt u mij niet zo. In English: Even if it comes very natural to me. Otherwise you do not understand me..

I would like to know what people, in this very worldwide community of Ubuntu users, think of this discussion. There are other conventions, such as BODMAS, and probably some that compute everything from left to right. And we in Holland had one that differed for historical reasons, started with Descartes when he was in Holland. How is it in France: also square roots having  a lower precedence than Multiplication and Division, so not needing brackets when writing the square root of (a times b)?

Topsiho

---

### Post by sudodus on 2023-04-19
> **Topsiho said:**
> Expressions as we see them today are only a very recent invention. In fact, they are a very concise way of describing a problem to solve. Modern mathematicians are not capable of solving problems as described before let's say the 1700's. Long winded and in a way that the mathematicians of their time could understand, but not those of this time.

It is like a language.
If someone starts speaking another language, he or she might be quite right, but doesn't get across what he/she wants to say.

There is a science that studies math in antiquity, very very much interesting. The Babylonians were extraordinary clever scientists in their time, but only a few scientists now understand their clay tablets.

We have some rules, PEMDAS is not used in all countries, and there are more rules. But if you agree on a set of rules, then you should stick to them, and not follow your instinct or what you think is better. My instinct is using my own language, which I know better and in which I (have learned to) think, but I have to stick here to English. Anders begrijpt u mij niet zo. In English: Even if it comes very natural to me. Otherwise you do not understand me..

I would like to know what people, in this very worldwide community of Ubuntu users, think of this discussion. There are other conventions, such as BODMAS, and probably some that compute everything from left to right. And we in Holland had one that differed for historical reasons, started with Descartes when he was in Holland. How is it in France: also square roots having  a lower precedence than Multiplication and Division, so not needing brackets when writing the square root of (a times b)?

Topsiho

Here are my two cents:

It is very interesting to think about this issue and to discuss how to manage cases that can be interpreted in different ways.

- My experience of modeling with computational tools makes me favor PEMDAS and to avoid ambiguous expressions.

- I am also interested in the other views and conclusions, how people think in order to favour other interpretations of the initial expression of this thread. There are many other examples where similar thinking and discussion would be useful (it is not limited to mathematical expressions, most of the examples I can think of are from other fields).

---

### Post by aytuggurbuz on 2023-04-26
I am sorry to say that your friend who is a genius at math probably isn't. Basic math, as provided step-by-step by others, dictates the answer is 36.

---

### Post by agentl074 on 2023-04-30
To be fair, I use a TI-83 -- not a computer calculator lol, but as others have mentioned, it could be how the calculation is 'asked'.

---

### Post by Keith_Beef on 2023-05-03
Would it have helped to convert to RPN (reverse Polish notation) beforehand?

48 8 / 14 8 - *

push 48
push 8
divide (equivalent to 48 / 8) results in 6

push 14
push 8
minus (equivalent to 14 -8) results in 6

multiply (equivalent to 6 * 60) results in 36

---

### Post by Topsiho on 2023-05-05
Yes, it helps :)

It also helps if you enter it differently in RPN.
The answer depends on** what is executed first: multiplication, or division**.
And that is the whole thing: using RPN you are the one who decides, in an algebraic calculator the calculator decides.
And that is why some calculators get this answer, and other calculators, even from the same manufacturer, get the other answer.

Note: are you sure you still use ubuntu 19.04? It is obsolete for a long time now!

---

