---
title: "Spacer or Indenter?"
date: 2008-02-29
forum: The Cafe
---

### Post by Glaxed on 2008-02-29
In a visual way, what type of coder are you?
Do you always indent, or do you use all spaces, or tabs and spaces?
Do other people understand your code when they see it?

I'm asking because I've always been a die-hard indenter, and spaced-out code confuses me.. I want to see what the general trend is.

I also have a bad habit of putting multiple 'expressions' of code in one line, as in;
int var; char var2;
instead of
int var;
char var2;.
Does anyone else find themselves doing this?

---

### Post by kaens on 2008-02-29
> **Glaxed said:**
> In a visual way, what type of coder are you?
Do you always indent, or do you use all spaces, or tabs and spaces?
Do other people understand your code when they see it?


I personally always use the tab button to indent, but set tabs to use spaces. (normally 4, sometimes less, sometimes varying depending on what type of code I'm writing). I've never had someone complain that my code was poorly formatted.


> 
I'm asking because I've always been a die-hard indenter, and spaced-out code confuses me.. I want to see what the general trend is.


I'm pretty sure the generally accepted rule is "never mix spaces and tabs" followed by a slightly weaker "tabs are really just a bit bad in general. tab-stops, on the other hand. . ."

> 
I also have a bad habit of putting multiple 'expressions' of code in one line, as in;
int var; char var2;
instead of
int var;
char var2;.
Does anyone else find themselves doing this?

Sometimes, but only when the variables are of the same type.

---

### Post by LaRoza on 2008-02-29
[Tabs, indents, spaces...]("http://ubuntuforums.org/showthread.php?t=502561") - Poll on coding styles

It depends on the language and purpose, but I usually don't put more than one statement on a line.

---

### Post by popch on 2008-02-29
When I last coded at all, I mostly used spaces to indent. That was only because some programs did something I didn't want when a line began with a tab.

Indenting with spaces was not much of a hardship because most of my code was short and shallow.

If it helped keeping the code to one page, I also would code several short statements on the same line. However, I never did so when it resulted in a statement becoming spread over two lines.

That worked well for Smalltalk and Prolog. 

It did not help so much for XSLT, where I used tabs and practically never put more than one statement to a line. XSLT is not particularly shallow, and the short statements aren't short, either.

---

### Post by ~LoKe on 2008-02-29
I use tabs and tabs only.  Spaces make it difficult to correct spacing and have it perfectly aligned.

---

### Post by LinuxMonk on 2008-03-02
> **~LoKe said:**
> I use tabs and tabs only.  Spaces make it difficult to correct spacing and have it perfectly aligned.

I use VIM, and have expandtab turned on (sets tabs to spaces).  Why is it difficult to correct spacing?  If I find a code block that's only two spaces off the left margin, I can just mark the first line of the block, go to the last line, and use a :'a,. s/^/  / to add two more spaces.  Dunno how that works in Emacs.

---

### Post by klange on 2008-03-02
I press tab, but it's set to insert 4 spaces.

---

### Post by Samhain13 on 2008-03-02
+1 for "tabs as spaces". :)

But then, I only write HTML, CSS and PHP. I don't know if it makes any difference when writing other things.

---

### Post by Nevon on 2008-03-02
I used to use tab, but now I've switched to two spaces per level.

---

### Post by Glaxed on 2008-03-02
I dont have anything against either, but it's when they get mixed up that it hinders me.

---

### Post by klange on 2008-03-02
> **Samhain13 said:**
> +1 for "tabs as spaces". :)

But then, I only write HTML, CSS and PHP. I don't know if it makes any difference when writing other things.

It helps a lot in Python as everything is clear and easy to see in every editor, unlike with tabs where you need to have some sort of "show whitespace" option to tell the difference easily.

---

### Post by SomeGuyDude on 2008-03-03
I'm an indenter AND a spacer. I'm extremely OCD about my code looking pretty (at least I was when I majored in CS). Each function was separate, and everything was nested. Lord help me if I had loops inside loops, I'd be seven or eight tabs in.

---

