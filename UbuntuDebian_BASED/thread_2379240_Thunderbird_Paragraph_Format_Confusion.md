---
title: "Thunderbird: Paragraph Format Confusion"
date: 2017-12-02
forum: Ubuntu/Debian BASED
---

### Post by lex24 on 2017-12-02
The "paragraph format" was introduced in Thunderbird's Composer in v45.0. It requires hitting Shift+Enter to insert a single line break. Hitting Enter will insert two line breaks (a "paragraph"). While this behaviour can be disabled in Preferences-Composition its effects linger in some unexpected situations (see point "2" below).

1) Can someone point to some knowledge base, FAQ, research paper, etc. that explains why on earth was that implemented? Is this feature used in some other office software, is it some new fashion trend?

2) I have noticed that it also affects Edit-Copy and Edit-Paste functionality. Here is an example (with the "paragraph format" mode disabled in Preferences):

Type text:

```
[SIZE=-1][SIZE=-1]This is a test line #1[/SIZE][/SIZE][SIZE=-1].[/SIZE]
```

Highlight that line, hit Ctrl+C - End key - Ctrl+V

```

[SIZE=-1][SIZE=-1]This is a test line #1[/SIZE][/SIZE][SIZE=-1].
[/SIZE]

 [SIZE=-1][SIZE=-1]This is a test line #1[/SIZE][/SIZE][SIZE=-1].[/SIZE]


```

Why is that? The "paragraph format" mode is disabled so it should be:

```

[SIZE=-1][SIZE=-1]This is a test line #1[/SIZE][/SIZE][SIZE=-1].[/SIZE][SIZE=-1][SIZE=-1]This is a test line #1[/SIZE][/SIZE][SIZE=-1].[/SIZE]

```

If you add space at the end of the line before hitting Ctrl+V it's even more unpredictable, and the behaviour also seems to change depending on how many times you repeat the process.

From what I can see you really need to use **Ctrl+Shift+V** instead of **Ctrl+V** regardless if the "paragraph format" mode is enabled or not, but I don't see it documented anywhere.

So in short, what are the "best practices" to deal with all that? Maybe we should just leave the "paragraph format" enabled and learn some new keyboard shortcuts.

---

### Post by walts48 on 2017-12-03
It was implemented because it was asked for in a Core:Editor bug report filed 17 years ago.

> In a normal situation, there is no reason to insert line breaks inside
paragraphs. Also, one expects Mozilla to behave consistently with word
processors and other HTML editors (including but not limited to Word,
AppleWorks, Dreamweaver and Amaya).

[https://bugzilla.mozilla.org/show_bug.cgi?id=92686](https://bugzilla.mozilla.org/show_bug.cgi?id=92686)

Also a Thunderbird:Message Compose Window bug report filed 12 years ago and fixed in Thunderbird 45.0.

[https://bugzilla.mozilla.org/show_bug.cgi?id=330891](https://bugzilla.mozilla.org/show_bug.cgi?id=330891)

What version of Thunderbird are you using for your examples?

Using your STR it works properly for me using, Mozilla/5.0 (X11; Linux x86_64; rv:52.0) Gecko/20100101 Thunderbird/52.5.0, installed from Ubuntu.

---

### Post by lex24 on 2017-12-04
Thunderbird v52.5.0
Xubuntu v14.04

I have enabled "paragraph format" and started using **Ctrl+Shift+V** instead of **Ctrl+V. **It's just a matter of getting used to. I havnen't used MS Word much, mostly plain text editors, so I didn't realize it was a standard behaviour.

---

### Post by speartip on 2017-12-04
Just off the point, but do you realize that your version of Xubuntu, hasn't been supported for the last 7 months!

---

### Post by lex24 on 2017-12-06
> **speartip said:**
> Just off the point, but do you realize that your version of Xubuntu, hasn't been supported for the last 7 months!

It is actually not Xubuntu but Linux Lite v2.8 and it's supported until 2019-04-30. It is Ubuntu v14.04 based distro with Xfce that's why I posted here, but I should have probably posted this on Linux Lite forums instead.

---

### Post by howefield on 2017-12-06
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

