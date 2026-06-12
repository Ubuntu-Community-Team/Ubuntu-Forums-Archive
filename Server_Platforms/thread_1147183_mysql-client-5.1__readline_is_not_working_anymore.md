---
title: "mysql-client-5.1  readline is not working anymore"
date: 2009-05-03
forum: Server Platforms
---

### Post by acron on 2009-05-03
Hi there,

after installing mysql-5.1 (which removed mysql-5.0) the readline abilities in mysql stopped working. 
eg Ctrl-r is not giving me a search.

Can someone verify this behavior?

I found the following in the [changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/m/mysql-dfsg-5.1/mysql-dfsg-5.1_5.1.31-1ubuntu2/changelog"):
Replaced --without-readline to --with-libedit to configure options, as
    --without-readline doesn't seem to do the right thing anymore.

I suppose this is related to readline or a replacement to readline. Still ldd does not report libreadline oder libedit or something... just ncurses...

Greets acron

OS: ubuntu jaunty

---

### Post by fansipans on 2009-05-15
It looks like libreadline was replaced with libedit. I'm not sure if Ctrl+R is supported in libedit.

I found this thread via google because upgrading to mysql-client-5.1 caused my ( libreadline .inputrc configured ) vi bindings to stop working.

I got my vi bindings back in mysql by doing the following:

```
echo "bind -v" > ~/.editrc
```

Thanks for the libedit tip!

---

### Post by chuckh1958 on 2009-07-21
For whatever reason, the version of mysql in the repo is now the non-gpl'ed version which uses editline instead of readline. I had to add create an .editrc file with the following lines to get ctrl-R and DELETE to work.

bind "\e[3~" ed-delete-next-char 
bind "^R" em-inc-search-prev

Alternately you could build the CLI from source or do what I'm gonna try next which is install rlwrap and alias the mysql command like this...

alias mysql='rlwrap -a mysql'

---

### Post by DeathWolf on 2009-09-20
thanks for the rlwrap tip!
This piece of software is gold:)

---

### Post by Stas Agarkov on 2009-09-21
Thanks, it works. But inconvenient create this file in your home directory for each user. I created these lines in the file /etc/editrc and /etc/inputrc, but MySQL does not read them :(
What can I do?

---

### Post by allauthors on 2009-10-29
This did not work for me.   I created a .editrc file, filled it with the commands suggested above, and got no luck in getting vi-style command-line editing to work in mysql client, nor in getting any style history searching working.  emacs style history browsing works ^p and ^n and the arrow keys work, but nothing I put in any file seems to alter that behavior or add searching (I'd be happy with either ^R or ESC/, though I'd prefer the latter of course.   Has anyone had any further experience/solutions for this problem?

---

### Post by s_p_a_r_k_y on 2009-11-15
I also tried the .editrc and its no longer working for me after I upgraded to karmic... really loved ctrl-r history searching and would like to get it back. having the delete key work again would be great as well.

---

### Post by s_p_a_r_k_y on 2009-11-15
> **s_p_a_r_k_y said:**
> I also tried the .editrc and its no longer working for me after I upgraded to karmic... really loved ctrl-r history searching and would like to get it back. having the delete key work again would be great as well.

I downgraded to 5.0 steps before downgrading

backup database either by cp /var/lib/mysql /var/lib/mysql.5.1 -R or by running mysqldump --all-databases -r /root/all.sql

Then remove these files from /var/lib/mysql mysql_upgrade_info and debian-5.1.flag

Then remove mysql with apt-get remove mysql-server-5.1 mysql-client-5.1

and add in the new (old) version of mysql with

apt-get install mysql-server-5.0 mysql-client-5.0

it will run over the db install again but should have all the DBs from before. Not recommended on production environment, I just did it on my laptop where I test my code so for me having ctrl-r was very important.

---

### Post by h1d on 2009-11-16
Has anyone fixed this at 5.1?

.editrc and rlwrap both do not work. Kind of makes me mad having have to keep retyping same queries...

Also, is 5.0 better for production server? I heard 5.1 is quite different.
Though it sounds like Ubuntu's decision is a bad one if it is, otherwise I'd like to stick with 5.1 and fix this issue...

---

### Post by laramichaels1978 on 2009-11-16
Hello! I just want to add my voice to the choir of those who are in pain because of Ctr-R and the other nice readline features no longer working in the mysql client since I upgraded to Karmic. : (

Any indication on how to fix this is most appreciated. Besides the approaches suggested above, I also tried recompiling the client from the source I got from mysql.com (5.1.40), but that didn't fix things, either.

Any advice would be terrific. : )

/lara

---

### Post by alter1 on 2009-11-21
Same problem for me.

I launched the mysql client with strace, and it does not seem to read .inputrc or .editrc

---

### Post by chuckh1958 on 2009-11-23
What do you get when you run "mysql --version"? I get "mysql  Ver 14.14 Distrib 5.1.37, for debian-linux-gnu (i486) **using  EditLine wrapper**"

---

### Post by alter1 on 2009-11-27
Yes I get the same :
mysql  Ver 14.14 Distrib 5.1.37, for debian-linux-gnu (i486) using  EditLine wrapper

but it doesn't even read my .editrc (as shown by strace)

Actually it doesn't read any files in my home dir.

---

### Post by jsilve1 on 2009-12-15
I fixed this by downgrading to mysql-client-5.0

Not really a solution, though, is it?

jeff@jeff-laptop:~$ mysql --version
mysql  Ver 14.12 Distrib 5.0.83, for debian-linux-gnu (x86_64) using readline 5.2


That one works.

---

### Post by mynyml on 2009-12-31
The rlwrap alias solution worked fine for me

```

$ sudo apt-get install rlwrap
$ cat ~/.bash_aliases
alias mysql='rlwrap -a mysql'
$ mysql -u root
mysqld> #vi bindings and ctrl+r search all working

```

On Karmic, mysql client v5.1.37

Thanks chuckh1958 for the tip.

---

### Post by ebvigmo on 2010-01-06
Installing rlwrap (apt-get) and putting this alias in my .bashrc file worked for me.  Thanks!

alias mysql='rlwrap -a mysql'

---

### Post by radostyle on 2010-01-25
I thought rlwrap was working, but I found that when I use less as my pager, which I do, then it intercepts the q command to quit the editor and the up/down arrows.  So rlwrap is not a solution for me.

This guy has a deb file for amd64 that fixes the issue.  He also has the diff for his debian/rules changes if you want to rebuild it yourself.
[http://wjd.nu/notes/2009#mysql-ubuntu-readline-delete-char](http://wjd.nu/notes/2009#mysql-ubuntu-readline-delete-char)

---

### Post by DorianX on 2010-01-27
For me, rlwrap fixed the delete issue, but it rendered all control-key combos, (Ctrl-R, Ctrl-D, etc) useless

---

### Post by Dan42 on 2010-02-23
Thanks, rlwrap worked for me (even when piping to [FONT="Courier NEW"]less[/FONT]), except that
1. I had to fix my history file: [FONT="Courier NEW"]replace '\\040' ' ' '\\134' '\\' -- ~/.mysql_history[/FONT]
2. ctrl-D doesn't work anymore... so I use ctrl-C

---

### Post by kcn_viper on 2010-03-14
For my part, using rlwrap -a mysql results in password getting printed on screen when logging into mysql database as well as the password remains in the history !

Otherwise rlwrap solution seems to be working, Control R definitely is working for backward search.

Thanks Dan42 for the mentioning the needed changes in history file.

- KCN

---

### Post by ivotron on 2010-04-05
tab completion doesn't work in rlwrap since the only key that invokes the passing of input from rlwrap down to the mysql client is the <Enter> key.

I'm really looking forward to Lucid since the Ubuntu devs have compiled this package against readline :)

---

### Post by Yauhen Dounar on 2010-04-26
Just recompile mysql-client with checkinstall from source with flags --without-server and --without-readline

---

### Post by Przemek_a on 2010-09-08
Submitted a bug for this, as I think IT IS A BUG:
[https://bugs.launchpad.net/ubuntu/+source/mysql-5.1/+bug/633129](https://bugs.launchpad.net/ubuntu/+source/mysql-5.1/+bug/633129)

---

### Post by chuckh1958 on 2010-09-08
I'm not certain it is a bug. There are licensing issues involved and the mysql monitor (client) program cant include readline on some platforms.

---

### Post by Przemek_a on 2010-09-08
What kind of licensing issues ? And why does that not apply to debian ? I thought they use similiar policy.

And btw there are readline packages available for ubuntu:

dpkg -l|grep readline
ii  libreadline-ruby1.8               1.8.7.249-2.1                   Readline interface for Ruby 1.8
ii  libreadline5                      5.2-6                           GNU readline and history libraries, run-time librarie
ii  libreadline6                      6.0-5                           GNU readline and history libraries, run-time librarie
ii  readline-common                   6.0-5                           GNU readline and history libraries, common files

(Ubuntu 9.10)

---

### Post by Przemek_a on 2010-09-12
OK, I can see readline is back in Lucid, so hoping karmic will be fixed too :)

---

