---
title: "php5-gd"
date: 2007-02-14
forum: Server Platforms
---

### Post by uncleclinto on 2007-02-14
Okay,

I hope this is the right place.  If it's not, please kindly direct me to the proper forum.  

I really really want to get gd up and running for my moodle.  When I attempt to install the php5-gd package, I get the error: php5-common 5.1.2-lubuntu3 required  php5-common 5.1.2-lubuntu3.4 marked for intallation.  Is it just me or does php5-common 5.1.2-lubuntu3.4 seem newer than php5-common 5.1.2-lubuntu3?  Do I need to downgrade in some way in order to get php5-gd running??  If so, how on earth do I do that?  Incidentally, if there's documentation that covers this somewhere out there, please direct me there.  I did find some RSS thing that looked like it answered my question, but apparently my firefox browser doesn't read "atom" or something and it all came up gibberish.

ps: I'm not a jedi master when it comes to command line syntax, so you really have to spell everything out for me.  Don't expect me to know a "sudo" goes at the beginning of a line unless you put it there.

---

### Post by jtc on 2007-02-14
Let us see if we can figure this out :) 

ISounds like you are using Ubuntu 6.06 (Dapper Daker)? I just installed php5-gd on such an Ubuntu-computer without any trouble what so ever. How did you try to install it? Apt-get, Adept, Synaptic?

If I were to guess I'd say your packages-database isn't entirely up-to-date, which then would result in such confusing dependencies. Try updating it, unless you know you already have done so.

```
sudo apt-get update
```

---

### Post by jtc on 2007-02-14
...or, I just realized I might have missunderstood something. Just for clarification. You did have PHP5 already installed, right?

---

### Post by uncleclinto on 2007-02-14
Okay... done.  I updated but got this message.  This looks like something I need to deal with but how?

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by uncleclinto on 2007-02-14
Yes, I do have php5 installed.  

[www.walterswebdesign.org/phpinfo.php](www.walterswebdesign.org/phpinfo.php)

---

### Post by jtc on 2007-02-14
Sounds like your /etc/apt/sources.list neads to be looked at. Feel free to paste it here.

---

### Post by uncleclinto on 2007-02-14
Sources.list:


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Brazen on 2007-02-14
Your sources.list is a little messy but it should work.  However, you should probably delete the last four lines, they are redundant.  In fact you have a few other redundant lines, why don't you clean it up to look like this:```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
```

After you do that, run this command and post the output:```
sudo apt-get update && sudo apt-get -y install php5-gd
```

---

### Post by jtc on 2007-02-14
Well, that source.list was perhaps not entirely consistent :-)

I assume you intend to use main, restricted and universe. What about multiverse?

Then I see you have the backports enabled, is that intentionally?

---

### Post by uncleclinto on 2007-02-14
> **jtc said:**
> Well, that source.list was perhaps not entirely consistent :-)

I assume you intend to use main, restricted and universe. What about multiverse?

Then I see you have the backports enabled, is that intentionally?

I don't even know what backports are.  The only reason my sources list looks like it does is I've added lines suggested by forum posts here when I was trying to get moodle up and running in the first place.

In terms of your comment about not being entirely consistent, are you referring to my list or the list Brazen suggested??  I don't want to use Brazen's list if there's something wrong with it.

---

### Post by jtc on 2007-02-14
I was refering to your list. I hadn't even seen Brazens post when I wrote mine.

I'd say your should clear your file entirely and go for the list he posted. Myself I'd leave out the lines dealing with backports, but it is possible you have some use for them. In that case it deals with newer versions of software packages.

More info about what the backports are you'll actually find if you read the comments in your current sources.list

---

### Post by Brazen on 2007-02-14
> **uncleclinto said:**
> I don't even know what backports are.  The only reason my sources list looks like it does is I've added lines suggested by forum posts here when I was trying to get moodle up and running in the first place.

In terms of your comment about not being entirely consistent, are you referring to my list or the list Brazen suggested??  I don't want to use Brazen's list if there's something wrong with it.

There's nothing wrong with my list! *slap*

---

### Post by uncleclinto on 2007-02-14
> **Brazen said:**
> There's nothing wrong with my list! *slap*

You're right *slap* (that was a Budweiser slap).

I used your list... updated... installed... AND PRAISE THE LORD moodle recognized gd.

Thanks a bunch!

---

### Post by Brazen on 2007-02-14
> **uncleclinto said:**
> You're right *slap* (that was a Budweiser slap).

I used your list... updated... installed... AND PRAISE THE LORD moodle recognized gd.

Thanks a bunch!

:D You're welcome.

---

### Post by biofedora on 2007-04-24
Hi, 
I am also trying to get GD up and running for my LAMP server (Ubuntu server 6.10). I used Brazen's source.lst and then:
    sudo apt-get update && sudo apt-get -y install php5-gd
but I still get the following:
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php5-gd

I would appreciate any help anyone can give me.
Thanks in advance.

---

### Post by cruzdelsur on 2007-07-04
Hi I tried Brazen´s source.list and I get same error.

why Brazen´s lines begin with http//us. ****    is it from us, right? if I am on other country it will work the same?

any way i am still here

I tried:

sudo apt-get install php5-gd

but i get following error message

E: couldn´t find package php5-gd

Apache is working, my soft versions are:
SO  ubuntu 7.07 (Linux ubuntu 2.6.20-15-server)
PHP Version 5.2.1
Apache/2.2.3 (Ubuntu)


what can I do?

THANKS!!!

---

