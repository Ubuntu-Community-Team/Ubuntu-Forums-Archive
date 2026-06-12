---
title: "Why do people say that grep is so powerful?"
date: 2013-10-30
forum: Ubuntu, Linux and OS Chat
---

### Post by noahsdev on 2013-10-30
The only thing I use grep for is to weed out results I don't want returned from a command. I have read tonnes of places that grep is 'so powerful' but they don't explain why. 
Just curious, thanks.

---

### Post by deadflowr on 2013-10-30
read what it can do
```
man grep
```

---

### Post by 1clue on 2013-10-30
The man page has a tiny fraction of it.  To really understand you have to learn regular expressions.  Don't just stop at a couple tutorials, go through the entire reference.  Grep and egrep can match to just about any character data, and more importantly it can match to a string which is NEAR some other string.

If you want a good example of a crazy regex, look up 'email regex' and see what you get.

---

### Post by sffvba[e0rt on 2013-10-30
*Thread moved to **The Cafe**.*

Not an Ubuntu support question.


404

---

### Post by rencemc on 2013-10-30
It's great when your programming/scripting. That's where its true power lies, in my opinion. You can parse data with it and extract
fields and values that you are interested in.

---

### Post by buzzingrobot on 2013-10-31
Regular expressions are leveraged throughout the standard toolset in any Unix/Linux/BSD/OS X:  In the shell, in grep, in awk, perl, etc., etc., etc.

Certainly not the most intuitive things to grasp, but knowing even a little bit is very useful.

---

### Post by vasa1 on 2013-10-31
[http://www.codinghorror.com/blog/2008/06/regular-expressions-now-you-have-two-problems.html](http://www.codinghorror.com/blog/2008/06/regular-expressions-now-you-have-two-problems.html)

---

### Post by varunendra on 2013-10-31
> **1clue said:**
> Grep and egrep can match to just about any character data, and more importantly it can match to a string which is NEAR some other string..
..and probably **Most** importantly, it is _super fast_ at what it does.

---

### Post by 1clue on 2013-10-31
> **buzzingrobot said:**
> Regular expressions are leveraged throughout the standard toolset in any Unix/Linux/BSD/OS X:  In the shell, in grep, in awk, perl, etc., etc., etc.

Certainly not the most intuitive things to grasp, but knowing even a little bit is very useful.

I find this sentiment all over.  I can't exactly say it's wrong, but I think it's misleading and tends to make beginners avoid regex at all cost.  That's a disservice to beginners who might otherwise tackle it as the difficult but achievable challenge that it is.

The first impression of regex (regular expressions) is gobbledygook.  The beginning learning curve is steep and highly technical.

Once you get past a certain point however, it DOES start to make sense.  There is a structure to it, and at that point it becomes intuitive.

Let's be completely truthful here:  Regular expressions allow extremely precise pattern matching for complex situations.  They're very fast, very exact and very compact.  Unfortunately they are not very universal.  There are at least a dozen flavors of regex that I know of, and they're all in pretty widespread use in different situations.  Not all of these are in UN*X though.

Fortunately enough, the UN*X-oriented regex is pretty consistent.  The flavor that egrep uses is an extension of what grep uses, for example.  That same regex library is used all over in Linux.  But if you go to Java you have to make adjustments.  If you go to a lot of programming editors, you can sometimes get more than one flavor of regex in the same editor.

If you REALLY want to take advantage of UN*X then you need to have at least passable regex skills.  Otherwise you'd just as well run Windows.  There's a big pot of gold at the end of this rainbow, and you can get some of the payoff before you reach the end of the trail.

Back when I learned it, in order to really learn it you went out and bought a book.  O'Reilly's "Regular Expressions" book was wonderful, I've bought 3 editions because like anything else that's used frequently, regex changes over time.  Now I think you can find most of the material online if you're persistent.

---

### Post by drmrgd on 2013-10-31
> **1clue said:**
> I find this sentiment all over.  I can't exactly say it's wrong, but I think it's misleading and tends to make beginners avoid regex at all cost.  That's a disservice to beginners who might otherwise tackle it as the difficult but achievable challenge that it is.

The first impression of regex (regular expressions) is gobbledygook.  The beginning learning curve is steep and highly technical.

Once you get past a certain point however, it DOES start to make sense.  There is a structure to it, and at that point it becomes intuitive.

Let's be completely truthful here:  Regular expressions allow extremely precise pattern matching for complex situations.  They're very fast, very exact and very compact.  Unfortunately they are not very universal.  There are at least a dozen flavors of regex that I know of, and they're all in pretty widespread use in different situations.  Not all of these are in UN*X though.

Fortunately enough, the UN*X-oriented regex is pretty consistent.  The flavor that egrep uses is an extension of what grep uses, for example.  That same regex library is used all over in Linux.  But if you go to Java you have to make adjustments.  If you go to a lot of programming editors, you can sometimes get more than one flavor of regex in the same editor.

If you REALLY want to take advantage of UN*X then you need to have at least passable regex skills.  Otherwise you'd just as well run Windows.  There's a big pot of gold at the end of this rainbow, and you can get some of the payoff before you reach the end of the trail.

Back when I learned it, in order to really learn it you went out and bought a book.  O'Reilly's "Regular Expressions" book was wonderful, I've bought 3 editions because like anything else that's used frequently, regex changes over time.  Now I think you can find most of the material online if you're persistent.


Very nicely said!

I don't know specifically how 'powerful' grep is.  But is certainly very, very useful, and I use it several times a day, all day long - and in other forms, like Perl's grep.  Here's one possible use, I like to call the needle in a haystack.  I have a directory containing 293 experiments worth of run data,and I want to find out which ones contain a specific element.  Grep and a little logic to the rescue (plus GNU parallel because I'm impatient!):

```

$ time parallel "grep -q "AMPL395582581" {} && echo "Found in: {}"" ::: *lowamps*
Found in: MCC-178_IX008_lowamps.tsv
Found in: MCC-181_IX006_lowamps.tsv
Found in: MCC-187_IX006_lowamps.tsv


real    0m0.918s
user    0m0.352s
sys     0m0.300s

```

Less than a second to tell me which experiment I need to be following up on for that particular sample.  Pretty good if you ask me!

---

### Post by buzzingrobot on 2013-10-31
> **1clue said:**
> I find this sentiment all over.  I can't exactly say it's wrong, but I think it's misleading and tends to make beginners avoid regex at all cost.  That's a disservice to beginners who might otherwise tackle it as the difficult but achievable challenge that it is.

The first impression of regex (regular expressions) is gobbledygook.  The beginning learning curve is steep and highly technical.

Once you get past a certain point however, it DOES start to make sense.  There is a structure to it, and at that point it becomes intuitive.

If you can't intuit it, if you have to learn what all the LIttle Squiggly Characters mean, it isn't intuitive.

Not a knock on regex --  so much as it is a deliberate knock on how we've degraded the word "intuitive".  Very little about using a computer is intuitive.

Now, I'm not arguing people shouldn't dive in.  Regular expressions are useful even if you learn only a bit.

---

### Post by varunendra on 2013-10-31
> **drmrgd said:**
> Here's one possible use, I like to call the needle in a haystack.  I have a directory containing 293 experiments worth of run data,....
When I didn't know about "modprobe -c" command, I simply used something like this -
```
grep -iR /lib/modules/$(uname -r)/kernel/drivers 10ec.*8172
```
..to find out which (and if any) drivers support a device whose device ID is [noparse]10ec:8172[/noparse], and it gave me the result within 10 seconds.
(the actual line that contains this info is like this - "alias pci:v0000**10EC**d0000**8172**sv*sd*bc*sc*i*")

It searches even in the binary files and returns their names as results, which is quite helpful in my particular case. And that directory contains exactly 2542 files in my system! :)

For single files, no matter how huge they are (like a 3-4 MB syslog), its speed is almost instantaneous.

Even without complex use of regular expressions, its available options make it so flexible and so useful that is enough to give it an edge over most of the similar tools. The speed is a huge plus.

---

### Post by 1clue on 2013-10-31
> **buzzingrobot said:**
> If you can't intuit it, if you have to learn what all the LIttle Squiggly Characters mean, it isn't intuitive.

Not a knock on regex --  so much as it is a deliberate knock on how we've degraded the word "intuitive".  Very little about using a computer is intuitive.

Now, I'm not arguing people shouldn't dive in.  Regular expressions are useful even if you learn only a bit.

So if I were to tell you that many of the operators in regex correspond to keyboard standard symbols for logical operators, does that change anything for you?

This stuff wasn't just pulled out of thin air.  Regex came out of organized, systematic approach toward parsing and analyzing text.  They used logical operators from mathematics, as adapted for keyboards, for the parts it was appropriate to do so.  They used fairly reasonable programming syntax for capture groups.  And so on.

You might not recognize these symbols but they're not random.  If a mathematician took a first-glance at regex, he would probably think it was very intuitive.

Seriously, we're not really talking about grep at this point.  We're talking about regular expressions.  Grep is, in my opinion, a thin wrapper around regex.  There are a bunch of command-line filters which make use of regex in different ways.  Grep, sed, awk, and more.  Some of them are very thin, meaning they do a very limited number of things with regex as the main feature.  Others (perl) are rich languages which ALSO support regex fully.  Just about every programming language I've seen in the past 10 years has pretty decent regex support even if it's a library.

---

### Post by JKyleOKC on 2013-10-31
> **1clue said:**
> Seriously, we're not really talking about grep at this point.  We're talking about regular expressions.  Grep is, in my opinion, a thin wrapper around regex.Are you aware of what the name "grep" means? You have to go back to the very early days of Unix to find it: "**G**lobal **R**egular **E**xpression and **P**rint" or "grep" since in those days, at 110 baud with TTY Model 33s, brevity was essential when it came to naming commands.

It's been said that those who ignore history are doomed to repeat it. It would be well worth while to go back and look at what was being done in the 1965-1975 period. While we've come a huge distance in many areas, we've actually lost functionality in a few. For instance, around 1967 I was working with a time-shared G-E system called RAES, the Remote Access Editing System. It consisted of three programs: ACE, the All-purpose Context Editor which was similar to but much more powerful than "ed," the original Unix text editor; RUNOFF, an adaptation of the original "roff" publishing program from MIT; and SPOT, Selective Printout Of Text, which was somewhat like "grep" but lacked the power of regular expressions. SPOT could only select lines via string matching, and had no way to anchor the search to either end of the line, or to ignore case when matching.

However, SPOT did have one feature that so far as I know is not available in any similar program today: It could be given a second parameter with which to identify "header" lines, and would then print the header line immediately before the "selected" line in the output.

Such a capability, of course, is well within reach today. Yesterday I spent a couple of hours implementing it by trial and error using "awk" so that I could locate 14 error lines inside a 250K text file representing the result of testing a 4.5-GB database for problems, and identify the three files that contained those 14 errors. Had I been up to date on my knowledge of awk's syntax, it would have been more like a couple of minutes. But my point is that the "universal" search utility for our favorite operating system seems to be missing this quite useful option, which was available to all G-E rmployees (at least, all who had access to RAES) more than 40 years ago!

---

### Post by Lars Noodén on 2013-11-01
> **1clue said:**
> ... Others (perl) are rich languages which ALSO support regex fully.  Just about every programming language I've seen in the past 10 years has pretty decent regex support even if it's a library.

It sounds like you are referring to Perl Compatible Regular Expressions.   Perl more or less redefined what people expect from regex.  Before that, [SNOBOL4](http://www.snobol4.org/)+ and, to a certain extent, [Icon](http://www.cs.arizona.edu/icon/) were the innovators but did not manage to establish an industry-wide syntax like perl did.

---

### Post by 1clue on 2013-11-01
@JKyleOKC:  No, I hadn't known what grep stood for.  Cool.

@Lars:  I was thinking of Perl and its regex, but also of a whole lot more.  Just about every language now supports regex to some degree.

I guess what I was getting at is that the power of grep is the power of regex, and regex is much more than just grep.  By learning regex, you're not just figuring out how to use one or 3 or 20 command-line tools on Linux.  It's an entire mindset of abstract evaluation of text which can be taken to any operating system and a huge variety of industries.

---

### Post by sha1sum on 2013-11-01
Dear Topic starter,

If all the talk about grep and regular expressions makes you dizzy:

Read chapter 19 of this book:
[http://www.linuxcommand.org/tlcl.php](http://www.linuxcommand.org/tlcl.php)

You can download it there for free. It will explain everything.

---

### Post by pqwoerituytrueiwoq on 2013-11-01
> **buzzingrobot said:**
> Regular expressions are useful even if you learn only a bit.
i agree with that, always annoying when i don't know enough (partial regEx experience)
> **buzzingrobot said:**
> how we've degraded the word "intuitive".  Very little about using a computer is intuitive.
i disagree with using the word we, but that word has become meaningless it is now just a fancy word people throw around to sound smart

---

