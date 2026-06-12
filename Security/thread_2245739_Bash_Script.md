---
title: "Bash Script"
date: 2014-09-25
forum: Security
---

### Post by gordie692 on 2014-09-25
I read on the CTV News about Bash what is that is it something you can download or am I safe I'm ruunning 14.04 Ubuntu and I do updates everyday just to make sure I'm up to date
Just curious

---

### Post by varunendra on 2014-09-25
Would have been easier to answer if you could tell us exactly 'What' you read about it that is troubling you.

Bash itself is just a 'Shell Interpreter' - something pre-installed in Linux/Unix systems that interprets the commands you give to the system (via terminal, or scripts, programs etc.).

A "Bash Script" is a plain text file that contains one or more commands that will run in a defined order or a simple order of their occurance once you execute (run) the script. Whether a bash script is safe or not depends on what it was made for and how safely it does that. It is just a tool. Foolish use of it can cause troubles despite good intentions.

---

### Post by QIII on 2014-09-25
If you are talking about Shellshock, just keep your system up to date.

Two patches have been pushed in as many days.

To test if you are vulnerable, run the following in the terminal:

```
env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
```

If the result is 

```
vulnerable
```

you do not have the patches applied.

If you get 

```
bash: warning: x: ignoring function definition attempt
bash: error importing function definition for `x'
this is a test

```

then the patches have been applied.

This does not mean there will not be more updates coming, so update at least daily.

---

### Post by gordie692 on 2014-09-26
Thanks guys just making sure I'm secured when installed ubuntu 14.04 I only mostly install from software center or it right in the kernel or linux system

---

### Post by gordie692 on 2014-09-27
Sorry abont the bash post I was just concerned was reading abit on it thought I'd post and make sure I'm secured I've been been doing my updates due to this

---

### Post by J Tinsby on 2014-09-27
> **gordie692 said:**
> Thanks guys just making sure I'm secured when installed ubuntu 14.04 I only mostly install from software center or it right in the kernel or linux system

fwiw running that script on my Ubuntu 14.04 indicated it was vulnerable, so if you haven't run the test script I'd suggest doing so.

good luck

J T

---

