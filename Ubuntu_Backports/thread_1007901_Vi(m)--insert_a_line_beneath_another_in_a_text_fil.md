---
title: "Vi(m)--insert a line beneath another in a text file globally"
date: 2008-12-10
forum: Ubuntu Backports
---

### Post by linuxhurts on 2008-12-10
Hey Everyone,

I am using Vi(m) text editor.  Version 7.0

What I'm trying to do is simple.

I have two unique lines in a text file with the word '$count++' on one line and '$count--' on the other line (it's a perl script).

I would like to paste the phrase 'system "clear";' (a perl function) beneath each line, throughout the entire document (globally).

It is 6,000 + lines of code!

How can I do this in a single command?

I'm comfortable with linux, vim and the shell, so whatever I have to do.

Thanks!

---

### Post by Dr Small on 2008-12-10
This can probably be done with sed.

---

### Post by andrew.46 on 2008-12-11
Hi,

You could use the 'append' option with sed. I don't think it can be done with a single line but these 2 commands will do what you want:

```
sed '/\$count++/ a\
system \"clear\";' filename > output_file
```

and then:

```
sed '/\$count--/ a\
system \"clear\";' filename > output_file
```

Can somebody more clever than me fix the regexp so both can match in one line?

  Andrew

**Edit:** Woo hooo!!! A few more careful moments seems to have produced a winner:

```
sed -e '/\$count++/ a\
system \"clear\";' \
-e '/\$count--/ a\
system \"clear\";' filename > output_file
```

I declare myself king of sed for 1 day :-).

---

### Post by lensman3 on 2008-12-11
According to Kernigan & Pike, "The Unix Programming Language", on page 326 in the appendix, the following should work.


1,$s/part1part2/part1\                    
part2/

the \/n addes a newline and should add your system call.

And for real fun, enter g/^/m0    this command will reverse all the lines in your 8000 line file.

---

