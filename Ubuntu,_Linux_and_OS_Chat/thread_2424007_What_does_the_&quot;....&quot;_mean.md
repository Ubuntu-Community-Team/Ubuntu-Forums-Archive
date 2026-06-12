---
title: "What does the &quot;../../&quot; mean?"
date: 2019-08-01
forum: Ubuntu, Linux and OS Chat
---

### Post by littleejido on 2019-08-01
Hello, 

I have seen "cp -r ../../PATH/". What does the "../../" mean? 

I have searched but cannot find an answer. 

Thanks!

---

### Post by SeijiSensei on 2019-08-01
../ refers to the parent of the current directory.  ../../ refers to the parent of the parent.  For instance,

```

cd /usr/share/dpkg
ls ../     # returns the directory listing for /usr/share
ls ../../  # returns the directory listing for /usr

```

The current directory can be represented as a single dot. Both it and .. will appear in a directory listing if you use "ls -la".

---

### Post by TheFu on 2019-08-01
In all popular computer operating systems, there is an idea of 
a) absolute paths
b) relative paths

Absolute paths begin with a / or whatever the directory separator might be.  In general, a / can be used, even on Windows.
Let's use your HOME directory as an example.  Assuming you didn't do anything funny, and your username is littleejido, then your HOME directory will be in 
/home/littleejido  that is the absolute path to it.

If your current working directory is /home, **cd /home** will get you there, then **cd littleejido** will take that specific shell/CLI/terminal into your HOME using a "relative path."  You could have used **cd ./littleejido** too, which is also a relative path.

Moving on.   You can get into your HOME for the current userid using any of these commands:
```
cd $HOME
cd ~
cd ~/
cd ~littleejido

``` all the same result.  If you are littleejido and want to get into userid's "joe" HOME and you are inside your HOME, then you can use, 
```
cd ~joe
cd ../joe
cd /home/joe
cd ../../home/joe

```

Clear as mud?

Being able to use relative paths can really save time typing.

If there are only 2 userids on the computer, joe and littleejido, and you are logged in as littleejido and inside littleejido's HOME, you can get into joe's HOME using some wildcards too.
```
cd ~joe
cd ../j*
cd /ho*/*e
cd ../../ho*/j*

```
The pattern used just needs to be unique enough to match 1 solution.

---

### Post by an-ordered-hole on 2019-08-03
It's what is called a 'relative' path and it's doing what the previous post have explained. It's an alternative to an absolute path which will list all parent directories. If you are familiar with HTML I believe the same convention is used to address links, images, and files. If you are not familiar with HTML just know this convention is used widely in markup and programming languages and not just in a bash terminal.

Now that I think of it, why does the convention uses two dots rather than just one?

---

### Post by TheFu on 2019-08-03
> **an-ordered-hole said:**
> Now that I think of it, why does the convention uses two dots rather than just one?

Because ./ is the current directory, so ../ is the parent.

This convention has been around since 1970 and pretty much every popular OS that isn't a mainframe uses it, including Windows.  In fact, in Windows, you can use cd ../../ instead of cd ..\..\ if you like - as a cross-platform software developer, we used this all the time in our code that ran on over 12 platforms.

Some shells, like zsh, support just adding dots to go up one more level.  [https://stackoverflow.com/questions/23456873/multi-dot-paths-in-zsh-like-cd](https://stackoverflow.com/questions/23456873/multi-dot-paths-in-zsh-like-cd)

Of course, you can create aliases in bash to do it that way too:
```
alias cd...='cd ../../../'
alias cd....='cd ../../../../'
```

Notice that my aliases don't have spaces ... so they appear as a command.

---

### Post by an-ordered-hole on 2019-08-04
Interesting. Also, if you run the
> 
**command(lists all files in current directory):**
 ls -la 

**output:**
drwxr-xr-x 31 hegel hegel  4096 Aug  3 20:49  .
drwxr-xr-x  3 root  root   4096 May  8 20:10  ..


The first two directories are . & .. and does that mean they are actual files. Like can you delete or change the name of '.'? Or are they just relative names?

---

### Post by TheFu on 2019-08-04
I think the OP's question was answered.  Start your own thread if you have a question.  Thread hijacking is to be avoided here.
In the meantime, you can look up "**everything is a file**" in wikipedia.

---

### Post by an-ordered-hole on 2019-08-07
1. The guy has not stated he's satisfied with the answers

2. Adding context to the original question serves to broaden understanding.  No question can be categorically answered by one person in a few posts.

3. You're extremely unfriendly/trolly.

Pretty sure you are to be avoided here.

---

### Post by wildmanne39 on 2019-08-07
Hello an-ordered-hole, if you have an answer then you are more then welcome to post it, if you have a question then you need to start your own thread as it gets confusing for the users being helped and the volunteers helping, TheFu is one of the most helpful volunteers here and we do not allow derogatory remarks about other members here, please read the forum rules here:

[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

If you have an issue with a post please use the report button in the lower left hand corner of he post to report it.

---

### Post by sdsurfer on 2019-09-03
This is all pretty well answered above . . . the following is strictly opinion and take it as you wish. I'd just like to add in scripting of almost any language I find this usage annoying. Larry Wall calls this "dot-toothpick" syntax and proposes lots of ways to avoid it in Perl, but his concepts apply to almost any scripting language.

*Why do you find it annoying?*

Developers spend most of their time scanning files, following code, every little thing we have to stop and think about is pretty much a waste of time. Wrangling with "where am I, and where is this telling me to look?" is tedious and often time consuming when I should be spending the time, well, coding. 

Second, if you ever need to move A Thing you have to find all the directory references and update them. Then fix them when you get the dots and toothpicks wrong.

Last, there are so many better ways to deal with directory traversal. Among them are setting environment variables defining paths (either system wide or app specific,) set down the rule to always start from root (absolute for CLI, domain-relative from HTTP,) or even better, use autoloaders and namespacing so you never have to figure out the dot-toothpicks ever again. :-)

Just IMO

---

