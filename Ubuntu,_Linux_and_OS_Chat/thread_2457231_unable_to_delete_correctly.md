---
title: "unable to delete correctly"
date: 2021-01-28
forum: Ubuntu, Linux and OS Chat
---

### Post by danielbernardograset on 2021-01-28
Am quite new to Ubuntu so this may sound to you like a bit silly question but... :confused:

Imagine you would like to delete this word: **eXamPle**

A key point to this question is that I press **ctrl + del** so that can remove both easier & quicker.

When running the Windows OS and deleting words using this combination of keys, it deletes the letters that are after the first capitalized letter. In this case, it would delete till **P **>> **eXamPle** would become **eXam**.

When running the Ubuntu OS 20.04.1 does not do the same. Instead, when pressing **ctrl + del **deletes everything...

Why is that ?

May I change it ?

Thx in advance !

---

### Post by TheFu on 2021-01-28
Huh?

I have no idea what you are talking about.  Which program?  The program controls how selections inside the program work, not the OS.  In general, a space or whitespace is used as the word separator on all OSes, but that would matter only in a shell where you can change the IFS to something else.  Each shell could handle the separator differently.  This is fairly esoteric, so you'll need to read and understand the manpage for the shell you use.  For example, the bash manpage about IFS:```

       The shell treats several parameters  specially.   These  parameters  may
       only be referenced; assignment to them is not allowed.
       *      Expands  to  the  positional parameters, starting from one.  When
              the expansion is not within double quotes, each positional param&#8208;
              eter  expands  to  a separate word.  In contexts where it is per&#8208;
              formed, those words are subject to  further  word  splitting  and
              pathname  expansion.   When  the  expansion  occurs within double
              quotes, it expands to a single word with the value of each param&#8208;
              eter  separated  by  the first character of the IFS special vari&#8208;
              able.  That is, "$*" is equivalent to "$1c$2c...", where c is the
              first  character  of  the  value  of the IFS variable.  If IFS is
              unset, the parameters are separated by spaces.  If IFS  is  null,
              the parameters are joined without intervening separators.
...
       IFS    The  Internal  Field  Separator  that  is used for word splitting
              after expansion and to split  lines  into  words  with  the  read
              builtin command.  The default value is ``<space><tab><newline>''.
...
       The shell treats each character of IFS as a delimiter,  and  splits  the
       results  of  the  other  expansions into words using these characters as
       field  terminators.   If  IFS  is  unset,  or  its  value   is   exactly
       <space><tab><newline>,  the  default,  then sequences of <space>, <tab>,
       and <newline> at the beginning and end of the results  of  the  previous
       expansions  are  ignored,  and any sequence of IFS characters not at the
       beginning or end serves to delimit words.  If IFS has a value other than
       the  default,  then sequences of the whitespace characters space and tab
       are ignored at the beginning and end of the word, as long as the  white&#8208;
       space  character  is  in the value of IFS (an IFS whitespace character).
       Any character in IFS that is not IFS whitespace, along with any adjacent
       IFS  whitespace  characters, delimits a field.  A sequence of IFS white&#8208;
       space characters is also treated as a delimiter.  If the value of IFS is
       null, no word splitting occurs.
```
There are many other parts of that manpage with IFS references, which could be critical to what you seek.

For example, in a bash shell, <cntl>-w will delete to the left until the next IFS character - since that's usually a whitespace, that would be the word to the left of the cursor.  Very handy. This is with emacs keybindings.  vi keybindings can be set too, if you prefer.

---

### Post by ajgreeny on 2021-01-28
In a text file opened in either a text editor such as gedit or mousepad Ctrl+Del will delete the whole word or part word to the right of the cursor and the same deletion happens to a word or part word to the left of the cursor when using Ctrl+Backspace.

Exactly the same thing happens in Libreoffice files, or all that I've tried so far.  I have also used the key combinations in this forum's reply box and once again it is the whole (or part) word, which is deleted.

None of this seems too surprising if you bear in mind that Ctrl+Left or Ctrl+Rt just moves the cursor in the same manner, ie, to either the end or beginning of the word depending on the key used with Ctrl, and using Del instead of cursor key would therefore be expected to delete text to the same point.

---

### Post by grahammechanical on 2021-01-28
According to these web sites Ctrl+Del will delete the next word in Windows. There is no mention of the action not deleting capital letters in that word.

[https://fmhelp.filemaker.com/help/15/fmp/en/index.html#page/FMP_Help/text-shortcuts-windows.html](https://fmhelp.filemaker.com/help/15/fmp/en/index.html#page/FMP_Help/text-shortcuts-windows.html)

[https://www.techrepublic.com/blog/microsoft-office/two-useful-word-shortcuts-for-quickly-deleting-text/](https://www.techrepublic.com/blog/microsoft-office/two-useful-word-shortcuts-for-quickly-deleting-text/)

As far as I can see the use of Ctrl+Del in Linux programs is the same as in Windows programs. Before the development of the Graphical User Interface and the use of a mouse as a pointer, all programs used keyboard shorts cuts to do everything. These shortcuts became standardized to make it easier for users to change to a rival program. Compatibility both in the hardware to run existing programs and between programs was an important point in making purchasing decisions back in the old days. Those were the days when purchasing a computer did not mean getting an OS and applications thrown in for the same price.

Regards

---

