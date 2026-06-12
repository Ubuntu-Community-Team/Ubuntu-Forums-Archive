---
title: "What should be the platform from Web development  newbie."
date: 2020-10-19
forum: The Cafe
---

### Post by martinharry339 on 2020-10-19
Please suggest your opinion and experience.

---

### Post by slickymaster on 2020-10-19
Not a support request.

Thread moved to **The Cafe**.

---

### Post by Dragonbite on 2020-10-19
The setup I keep working on 

Linux desktop
LXC/LXD or KVM for web service (SSH, LAMP)
- LXC/LXD and KVM give you a Linux container or VM but since you are working in Linux already, you could bypass this and install the LAMP server right on your desktop directly
Visual Studio Code with Remote SSH to access the server
phpMyAdmin for easy database management


Currently I am running Windows on my desktop so my current setup is more like:

Windows desktop
WSL for LAMP server
 - mount  the /var/www directory of WSL with somewhere accessible through Windows for easy file-transferring
Visual Studio Code with Remote WSL to access the server
phpMyAdmin for easy database management

---

### Post by sdsurfer on 2020-10-19
Web development in what language or languages?

It's really going to vary. If you're working in Linux/Ubuntu, open source 'wares are going to be useful. A good IDE (below) for coding, git or SVN for version control, a local working environment (also below,) Gimp works great for graphics, OpenShot is one of the great and simple video editors, and some sort of way to move files from your local development environment (below) to staging and production. The "usual" way is via FTP. Personally I like using git for deployment, commit changes locally to master, then go to the target location which also runs off master and pull in the updated master branch. No fiddling with moving files around, update master, SSH to the production site, update master from the repo, done. If something goes wrong, reset master back one in prod.

If you are doing client-side work - design, layout, Javascript-based GUI's etc. - a familiarity with the various Inspectors in all browsers is critical.

An understanding of databases is important for server side development in any language. Most start with MySQL, but others - Postgres, Mongo, etc. - have advantages over MySQL that may be leveraged.

If you're working on Linux, you will need to know how to run a virtual machine so you can cross-browser test your work in Windows browsers. Recently I worked on a project that had issues with JAWS, the most common Windows-based screen reader. Don't ignore universal access if you're developing client side.

The local development environment is critical. In Linux you already have it, the Apache (2) server that defaults to /var/www/html on localhost. You may want to fiddle with this, it's very useful to set up "tests.com" or "mysite-test.com" locally so you can browse to multiple projects. In Windows this is done using the LAMP server, but that's really most effective if you're developing server-side apps in PHP, like Wordpress.

***The absolute most important thing*** to create clean, bug-free code is an IDE you can tailor to your language of choice. When I started decades ago, I developed in Notepad. (!!!!!!) I thought I really stepped up my game when Macromedia Homesite came around, it highlighted syntax, created templates, did a lot of the repetitive stuff for me. How little I knew. :-D

When I saw one of my Homesite projects in Netbeans (open source and free) for the first time, I was appalled. The built-in code checking functions pointed out all my unused and undefined variables, inefficient syntax, literal hard errors, and other garbage I'd overlooked. It showed me where the function/method docblocks were indicating wrong or missing params, which is really important if you use a documenting system that makes use of these. Searching for code blocks literally ceased - you can control-click on a function call and it will take you right to the function/method. Control-click the function declaration, it lists everywhere it's called. 

Then I discovered PhpStorm, and it is even better but it is not open source or free. If you make one investment in your career, make it an investment in one of the JetBrains products tailored for your language. It has additional features, one of which is to tell you whether your code is adhering to the PSR's (for PHP) and if your code contains deprecated elements for a given language. It formats your code correctly, to standard, so all your code is the same. Settings can be exported so the entire team codes exactly the same way (or should, it's really hard to convince a team this is important.) There's tons more, if you're serious about a career in web development, JetBrains products are well worth the investment.

Many will tell you that now you're using the IDE as a crutch, you are changing your code to make the IDE "happy," but that IMO is all ego talk. If there is one thing I could impress on web dev newbie, it is to invest in a good IDE, trust it, and use it to it's fullest ability. It will improve your code and make you a better developer and better yet it will help you code faster.

---

### Post by TheFu on 2020-10-19
What languages?
What sort of programs?
Are they micro-services, normal REST APIs, or full web-apps for end-users?

I consider any IDE to be a mistake.  A programmer who can be efficient with a good editor, good debugger, and good technique is worth all the IDEs on offer today.  Unix **is** an IDE already.  People hindered by "Windows-think" miss that fact.  

[https://sanctum.geek.nz/arabesque/series/unix-as-ide/](https://sanctum.geek.nz/arabesque/series/unix-as-ide/) explains. There are lots of other how-to guides, but basically, a few terminal windows opened and placed consistently provides the IDE experience that is consistent, provides direct access to the latest tools, and allows for unlimited customization based on the language, skills, automation, team work needed for a project regardless of language or other tools selected.

A good editor does all the tagging, function/class lookups, completion, and syntax highlighting. No need for heavy IDE. Jut learn to use a real programmers editor., probably one with thousands of extensions for every need tat doesn't need 8G RAM to load.

---

### Post by SeijiSensei on 2020-10-20
Like TheFu I do all my coding in an editor (jed, a clone of Emacs).  I write in PHP.  I prefer to use PostgreSQL over MySQL (or MariaDB) for various reasons.  Still the easiest solution on Ubuntu is to install the LAMP (Linux-Apache-MySQL-PHP) meta-package:
```
sudo apt install lamp-server^
```
which will install all the packages and any needed interstitial code. (Make sure you have the circumflex "^".)

When everything is set you should be able to create a file called "hello.php" in the root of the web server (/var/www/html) with the line
```
<?php echo "Hello, World!" ?>
```
and display that page with [http://localhost/hello.php](http://localhost/hello.php).

---

### Post by sdsurfer on 2020-10-22
> **TheFu said:**
> I consider any IDE to be a mistake.

Heh. So did I, until I saw my code in a really good one. It's got way more to do with creating compliant standardized code than any debugger or code tidy can do. I used all those before getting a good IDE as well, as above, so many things I never thought about became obvious.

---

### Post by coffeecat on 2021-04-14
The OP hasn't been back since the day they posted their one and only post on this forum. No point in allowing this thread to be necromanced any more. It will only attract spammers. Closed.

---

