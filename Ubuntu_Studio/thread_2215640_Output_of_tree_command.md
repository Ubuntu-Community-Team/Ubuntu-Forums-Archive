---
title: "Output of tree command"
date: 2014-04-07
forum: Ubuntu Studio
---

### Post by Pat C on 2014-04-07
I was saving output of tree command to file (*.docx) using this command in my Terminal Emulator:
      
   tree [PartitionName] -f -i -o [PartitionName]/[FileName]

 In addition to my desired information was the following unwanted outputs:

#[01;34m 
 #[01;35m 
 #[00m
 
 I have 2 questions:
What do those outputs mean?
How do I omit it from the output file?

---

### Post by steeldriver on 2014-04-07
They look like ANSI codes to specify text colors - you should be able to turn off colorization by adding the -n switch

```
tree [PartitionName] **-n** -f -i -o [PartitionName]/[FileName]
```

From *man tree*:
```

       -n     Turn colorization off always, over-ridden by the -C option.

```

---

### Post by sudodus on 2014-04-07
Yes, they are ansi escape sequences for controlling the colour of the output

You can use the following commands to see, what it looks like:

```
/bin/echo -e "\0033[01;34m hello world"
/bin/echo -e "\0033[01;35m hello world"
/bin/echo -e "\0033[00m hello world"
```

See this link

[https://en.wikipedia.org/wiki/ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

---

### Post by Pat C on 2014-04-07
Thanks for the info! :)

---

