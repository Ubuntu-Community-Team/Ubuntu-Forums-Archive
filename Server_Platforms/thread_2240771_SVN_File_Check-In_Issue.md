---
title: "SVN File Check-In Issue"
date: 2014-08-22
forum: Server Platforms
---

### Post by fret669 on 2014-08-22
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I am trying to get an svn server going on my site. Everything is going well. I can browse my repository tree with apache, and can check out my empty projects with no issues. The problem comes when I want to import an existing project to my repo. I can commit folders without issue, but any file I try to commit gives me a "Unexpected http status 500 'internal server error'" [/COLOR]

[COLOR=#000000]I have given my user access to the repository, and the folder has the correct permissions since I can view the files, as well as commit a folder... What could be causing this?[/COLOR]

[COLOR=#000000]Thank you,[/COLOR]

---

### Post by steeldriver on 2014-08-22
can you share the exact ci command?

---

### Post by fret669 on 2014-08-22
***SOLVED***

Virtual host location root cannot be "/". I changed it to "/svn", and everything is fine.

Repository:

    -Doesn't matter what type of tree I make in here
    - "svnadmin create /home/svn"
    - "svnadmin create /home/svn/reponame"
    - "chown -R svnuser:www-data /home/svn"
    - "chmod -R g+rws /home/svn"

Local Machine:

    - "svn checkout [http://svn.my-site.com/reponame](http://svn.my-site.com/reponame) --username USER" >> Successful download
    - Copy all files from a project I have been working on into the newly downloaded directory.
    - cd into this downloaded directory.
    - "svn add *"
    - "svn commit (or svn ci) --username USER" >> svn: E175002: Unexpected HTTP status 500 'Internal Server Error'

Now, if I make a folder called "TESTDIR" and use "svn add TESTDIR" and "svn commit", the directory uploads without issue.
If I make a file called "TESTFILE" and use "svn add TESTFILE" and "svn commit", I get the error shown above.

This is a password protected repository, but I know this is working because I can browse the repo online, as well as checkout the initial repo.

*EDIT: I also did a chmod 777 on my local folder to see if that would help. No dice.

I also found that for some reason my compiled objects in the folder will upload fine (not directly created by me), but no other files will.
Thank you,

---

### Post by fret669 on 2014-08-25
*bump*

---

