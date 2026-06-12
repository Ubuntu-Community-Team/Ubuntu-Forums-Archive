---
title: "Help - Shell Program"
date: 2006-04-15
forum: The Cafe
---

### Post by 008325 on 2006-04-15
i start to learn the shell program , 

i know that i can use >> to add sth to the file 

however , i dunno how to edit it after i add it ( delete or update )

plx help :D

---

### Post by PatrickMay16 on 2006-04-15
Dunno what you mean, but this could be helpful to you:
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by taurus on 2006-04-15
If you want to edit a file, use gedit (for GUI) or nano (if you don't have X running)!  And if you want to remove a file, use rm...
```

gedit filename <-- to use GUI...
-or-
nano filename <-- to edit it in a terminal...
rm filename <-- to remove a file...

```

---

### Post by 008325 on 2006-04-15
Sorry , i think that i should show some example to show ..what i am talking about

Example 

Fisrt , i have a artist file which contain some information

1. cat artist 

artist 1
artist 2
artist 3

i can use the command to add some information to file

2.  echo artist 4 >> artist 


artist 1
artist 2
artist 3
artist 4


====

so now , how can i edit or delete the artist file , e.g delete the artist 4


i hope you can understand ~THX

---

### Post by Stormy Eyes on 2006-04-15
[QUOTE=008325]so now , how can i edit or delete the artist file , e.g delete the artist 4

i hope you can understand ~THX[/QUOTE]

Try using nano. It's a text editor for the shell geared towards people new to the shell. Invoke it with the following command:
```
nano -w $filename
```
The "-w" switch turns on wrapping.

---

### Post by M7S on 2006-04-15
I think sed is a good option for removing lines from files but I can't remember the exact command for that. The answer is probably in the man-pages.

---

### Post by tseliot on 2006-04-15
[QUOTE=008325]so now , how can i edit or delete the artist file , e.g delete the artist 4


i hope you can understand ~THX[/QUOTE]
Do you want to delete the line without using a text editor, i.e. using a single command in bash?

---

### Post by aysiu on 2006-04-15
[QUOTE=M7S]I think sed is a good option for removing lines from files but I can't remember the exact command for that. The answer is probably in the man-pages.[/QUOTE] The answer probably is in the man pages somewhere, but am I the only one for whom man pages seem like a completely foreign language? Do these things actually make sense to programmers (I'm asking this question in all sincerity)? ```
SED(1)                                                                User Commands                                                               SED(1)

NAME
       sed - manual page for sed version 4.1.4

SYNOPSIS
       sed [OPTION]... {script-only-if-no-other-script} [input-file]...

DESCRIPTION
       Sed  is  a  stream  editor.   A stream editor is used to perform basic text transformations on an input stream (a file or input from a pipeline).
       While in some ways similar to an editor which permits scripted edits (such as ed), sed works by making only one pass over the  input(s),  and  is
       consequently  more  efficient.  But it is sed’s ability to filter text in a pipeline which particularly distinguishes it from other types of edi&#8208;
       tors.

       -n, --quiet, --silent

              suppress automatic printing of pattern space

       -e script, --expression=script

              add the script to the commands to be executed

       -f script-file, --file=script-file

              add the contents of script-file to the commands to be executed

       -i[SUFFIX], --in-place[=SUFFIX]

              edit files in place (makes backup if extension supplied)

       -l N, --line-length=N

              specify the desired line-wrap length for the ‘l’ command

       --posix

              disable all GNU extensions.

       -r, --regexp-extended

              use extended regular expressions in the script.

       -s, --separate

              consider files as separate rather than as a single continuous long stream.

       -u, --unbuffered

              load minimal amounts of data from the input files and flush the output buffers more often

       --help display this help and exit


       --version
              output version information and exit

       If no -e, --expression, -f, or --file option is given, then the first non-option argument is taken as the sed script to interpret.  All remaining
       arguments are names of input files; if no input files are specified, then the standard input is read.

       E-mail bug reports to: bonzini@gnu.org .  Be sure to include the word ‘‘sed’’ somewhere in the ‘‘Subject:’’ field.

COMMAND SYNOPSIS
       This is just a brief synopsis of sed commands to serve as a reminder to those who already know sed; other documentation (such as the texinfo doc&#8208;
       ument) must be consulted for fuller descriptions.

   Zero-address ‘‘commands’’
       : label
              Label for b and t commands.

       #comment
              The comment extends until the next newline (or the end of a -e script fragment).

       }      The closing bracket of a { } block.

   Zero- or One- address commands
       =      Print the current line number.

       a \

       text   Append text, which has each embedded newline preceded by a backslash.

       i \

       text   Insert text, which has each embedded newline preceded by a backslash.

       q      Immediately quit the sed script without processing any more input, except that if auto-print is not disabled  the  current  pattern  space
              will be printed.

       Q      Immediately quit the sed script without processing any more input.

       r filename
              Append text read from filename.

       R filename
              Append a line read from filename.

   Commands which accept address ranges
       {      Begin a block of commands (end with a }).

       b label
              Branch to label; if label is omitted, branch to end of script.

       t label
              If  a  s/// has done a successful substitution since the last input line was read and since the last t or T command, then branch to label;

              if label is omitted, branch to end of script.

       T label
              If no s/// has done a successful substitution since the last input line was read and since the last t or T command, then branch to  label;
              if label is omitted, branch to end of script.

       c \

       text   Replace the selected lines with text, which has each embedded newline preceded by a backslash.

       d      Delete pattern space.  Start next cycle.

       D      Delete up to the first embedded newline in the pattern space.  Start next cycle, but skip reading from the input if there is still data in
              the pattern space.

       h H    Copy/append pattern space to hold space.

       g G    Copy/append hold space to pattern space.

       x      Exchange the contents of the hold and pattern spaces.

       l      List out the current line in a ‘‘visually unambiguous’’ form.

       n N    Read/append the next line of input into the pattern space.

       p      Print the current pattern space.

       P      Print up to the first embedded newline of the current pattern space.

       s/regexp/replacement/
              Attempt to match regexp against the pattern space.  If successful, replace that portion matched with  replacement.   The  replacement  may
              contain  the  special  character  &  to refer to that portion of the pattern space which matched, and the special escapes \1 through \9 to
              refer to the corresponding matching sub-expressions in the regexp.

       w filename
              Write the current pattern space to filename.

       W filename
              Write the first line of the current pattern space to filename.

       y/source/dest/
              Transliterate the characters in the pattern space which appear in source to the corresponding character in dest.

Addresses
       Sed commands can be given with no addresses, in which case the command will be executed for all input lines; with one address, in which case  the
       command will only be executed for input lines which match that address; or with two addresses, in which case the command will be executed for all
       input lines which match the inclusive range of lines starting from the first address and continuing to the second address.  Three things to  note
       about  address  ranges:  the  syntax  is  addr1,addr2 (i.e., the addresses are separated by a comma); the line which addr1 matched will always be
       accepted, even if addr2 selects an earlier line; and if addr2 is a regexp, it will not be tested against the line that addr1 matched.

       After the address (or address-range), and before the command, a !  may be inserted, which specifies that the command shall only  be  executed  if
       the address (or address-range) does not match.

       The following address types are supported:

       number Match only the specified line number.

       first~step
              Match  every  step’th  line  starting  with  line  first.  For example, ‘‘sed -n 1~2p’’ will print all the odd-numbered lines in the input
              stream, and the address 2~5 will match every fifth line, starting with the second. (This is an extension.)

       $      Match the last line.

       /regexp/
              Match lines matching the regular expression regexp.

       \cregexpc
              Match lines matching the regular expression regexp.  The c may be any character.

       GNU sed also supports some special 2-address forms:

       0,addr2
              Start out in "matched first address" state, until addr2 is found.  This is similar to 1,addr2, except that if addr2 matches the very first
              line of input the 0,addr2 form will be at the end of its range, whereas the 1,addr2 form will still be at the beginning of its range.

       addr1,+N
              Will match addr1 and the N lines following addr1.

       addr1,~N
              Will match addr1 and the lines following addr1 until the next line whose input line number is a multiple of N.

REGULAR EXPRESSIONS
       POSIX.2  BREs  should  be supported, but they aren’t completely because of performance problems.  The \n sequence in a regular expression matches
       the newline character, and similarly for \a, \t, and other sequences.

BUGS
       E-mail bug reports to bonzini@gnu.org.  Be sure to include the word ‘‘sed’’ somewhere in the ‘‘Subject:’’ field.  Also, please include the output
       of ‘‘sed --version’’ in the body of your report if at all possible.

COPYRIGHT
       Copyright © 2003 Free Software Foundation, Inc.
       This  is  free  software;  see the source for copying conditions.  There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR
       PURPOSE, to the extent permitted by law.

SEE ALSO
       awk(1), ed(1), grep(1), tr(1), perlre(1), sed.info, any of various books on sed, the sed FAQ (http://sed.sf.net/grabbag/tutorials/sedfaq.txt),
       http://sed.sf.net/grabbag/.

       The full documentation for sed is maintained as a Texinfo manual.  If the info and sed programs are properly installed at your site, the command

              info sed

       should give you access to the complete manual.

sed version 4.1.4                                                     December 2005                                                               SED(1)
```

---

### Post by IYY on 2006-04-15
To delete a single line (in this case line #3) using sed:

```
sed -e '3d' filename
```

To delete a range of lines (in this case lines #1-3):

```
sed -e '1,3d' filename
```

To add a line at a specific place in the file (in this case, add line "hello world" as line 3):

```
sed  -e '3ihello world' filename
```

There's much more you can do using sed... It's like an entire language.

Note: the output of this is to standard output (the screen). If you want to overwrite on your original file, add a **-i** arg to the command.

---

### Post by 008325 on 2006-04-16
thank all for you

i still have two  question

1. how can i get the line number with grep or cut command ?

2. how to get the cut command return value ?

because i want to do this 

if [ "cut -f1 -d ',' database" == "1" ]; then
....
fi

something like that ( of couse , the above is wrong )

---

### Post by M7S on 2006-04-16
[QUOTE=aysiu]The answer probably is in the man pages somewhere, but am I the only one for whom man pages seem like a completely foreign language? Do these things actually make sense to programmers (I'm asking this question in all sincerity)?[/QUOTE]
Well, to be honest, if I would easily understand that man page, I would have written down the correct line right away. Maybe I should have mentioned google instead, since that was what I used when I needed sed myself...

---

### Post by 008325 on 2006-04-16
[QUOTE=008325]thank all for you

i still have two  question

1. how can i get the line number with grep or cut command ?

2. how to get the cut command return value ?

because i want to do this 

if [ "cut -f1 -d ',' database" == "1" ]; then
....
fi

something like that ( of couse , the above is wrong )[/QUOTE]

push

---

### Post by IYY on 2006-04-16
For grep, you add the **-n** option to get the line number (if you want -only- the numbers, you could then pipe it to **cut -d\: -f1**

I don't think it can be done with cut though. You'll need to find a different command.

---

### Post by 008325 on 2006-04-16
```
while [ "$ctrack" == "" ] 
	do
	read -p "Input something , if u want to stop , just press enter" ctrack
	echo "$ctrack"
        done
```

thanks a lot

sorry , maybe i ask too many question

why does the above statment wrong ?

i want the user press enter to stop the loop

but if i use above statment , the shell pass the loop ( do nothing , no ask the user to input )

---

### Post by IYY on 2006-04-16
The default value of $ctrack is "". If you want, you can assign it some other value before starting the loop (any value will do). So...

```

ctrack="something"
while [ "$ctrack" == "" ] 
do
	read -p "Input something , if u want to stop , just press enter" ctrack
	echo "$ctrack"
done

```

---

### Post by 008325 on 2006-04-16
[QUOTE=IYY]The default value of $ctrack is "". If you want, you can assign it some other value before starting the loop (any value will do). So...

```

ctrack="something"
while [ "$ctrack" == "" ] 
do
	read -p "Input something , if u want to stop , just press enter" ctrack
	echo "$ctrack"
done

```[/QUOTE]

thx a lot , i am sorry , i am too stupid ...

---

### Post by 008325 on 2006-04-17
i have a program again , i get the line number 

how can grep that line ?

i tried many command

example 

i got that string , and i know that it is in line 3

then , how can i grep all the information from line 3 ?

---

### Post by IYY on 2006-04-17
If you want to display the entire line that contains a specific string, then that's what grep does by default:

grep something somefile.txt

will return all lines that contain the word "something"

If you just have a line number and want to get the line, you can't use grep. There are several approaches that work, but one that comes to mind is:

yourcommand | head -n# | tail -n1

where # is the line number you want. for example

cat file.txt | head -n10 | tail -n1

will give you line #10 in file.txt

---

### Post by xenmax on 2006-04-17
[QUOTE==008325]i have a program again , i get the line number 

how can grep that line ?[/QUOTE]
I cant see where you are coming from here - like IYY said, by default grep displays entire line that matches and also displays line number if you pass -n option.
Perhaps, you want to display only one matching line at one time? If so, then your question makes more sense. You can also look at -m <number> option if it suits your requirements where you can specify how many matches(again, this is = lines) to display. For ex, grep -m 1 will only display first matching line.

If you still need to display just a particular line given the line number,
```
sed -n 'number,number,p' filename
```
should do it. [ -n is for quiet; p is for print - to print specified range ]
But note that in your program, if you want to get line number from output of grep, you may have to store it in a variable and post-process it.

---

