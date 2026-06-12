---
title: "What is this terminal behavior called?"
date: 2012-05-13
forum: The Cafe
---

### Post by Ranko Kohime on 2012-05-13
Sometimes, when I type a command incorrectly, I get a "greater-than" prompt after hitting enter, instead of a normal error message.

What exactly is that?  I suspect it's some type of command debugging console, but I have no idea what it's called to go searching for it, either in man or online.

For reference, I really only use the BASH shell, and this command causes the specific behavior I'm talking about:

```
for file in *; do fntsample -f "$file" -o ~/Downloads/fonts/"$file"
```

---

### Post by Copper Bezel on 2012-05-13
It's something related to the interactive mode for one of the commands you've run. The *at* command does this in normal operation. But I've had this happen, too, that I run a command that doesn't, to my knowledge, *have* an interactive mode but found myself at the weird little prompt and had to Ctrl+C out and try again.

---

### Post by sanderj on 2012-05-13
> **Ranko Kohime said:**
> Sometimes, when I type a command incorrectly, I get a "greater-than" prompt after hitting enter, instead of a normal error message.

What exactly is that?  I suspect it's some type of command debugging console, but I have no idea what it's called to go searching for it, either in man or online.

For reference, I really only use the BASH shell, and this command causes the specific behavior I'm talking about:

```
for file in *; do fntsample -f "$file" -o ~/Downloads/fonts/"$file"
```

It happens because your command is syntactically not finished / complete as the 'done' is not yet typed in. So:

```
for file in *z ; do echo 'hello' ; done

```
is a complete and won't give the prompt.

However, 

```
for file in *z ; do echo 'hello'

```
will give the prompt, until you type "done".

HTH

---

