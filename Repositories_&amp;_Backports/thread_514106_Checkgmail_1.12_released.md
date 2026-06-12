---
title: "Checkgmail 1.12 released"
date: 2007-07-31
forum: Repositories &amp; Backports
---

### Post by banana989 on 2007-07-31
How would I go about submitting a new build, and what is the build process?

---

### Post by F-3582 on 2007-08-02
> **banana989 said:**
> How would I go about submitting a new build, and what is the build process?
Sorry, but I never install this one via packages, because the whole installation process is ridiculously easy. Just download the thing from its homepage and unpack it into your /usr/bin directory. That pretty much does it.

---

### Post by hyperair on 2007-09-21
What about GTK2-Sexy?

---

### Post by ulli.winter on 2007-10-09
[http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu](http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu)
is this the only way to install gtk2 sexy?
way too much interaction for my taste with that cpan thing ;))

sorry, but i've got no idea how to submit the new build....

---

### Post by hyperair on 2007-10-09
About the Gtk2-Sexy, it's simple enough to install it via the CPAN method. After the initial set up, just keep pressing enter all the way xD

---

### Post by F-3582 on 2007-10-09
> **ulli.winter said:**
> [http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu](http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu)
is this the only way to install gtk2 sexy?
way too much interaction for my taste with that cpan thing ;))

sorry, but i've got no idea how to submit the new build....
Installing libsexymm2 from the repos is probably easier ;)

You should always check for recommended packages in Synaptic.

---

### Post by ulli.winter on 2007-10-09
recommandation.. for which package?

installed libsexymm2 - still getting "CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN" and clickable urls dont work

---

### Post by F-3582 on 2007-10-10
> **ulli.winter said:**
> recommandation.. for which package?

installed libsexymm2 - still getting "CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN" and clickable urls dont work
Right-click the checkgmail package and go into the "Recommended..." sub-menu.

Oh, and sorry. I forgot that checkgmail was Perl and not Python. Therefore the recommendations for checkgmail aren't sufficient, because Ubuntu is missing those Perl bindings for libsexy. Sorry for being smartass.

P.S.: Bug [filed]("https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/151226").

---

### Post by Greg T. on 2008-01-01
When I attempt to make GTK2-sexy, I'm greeted with the following error:

> mkdir /usr/local/man: File exists at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
make: *** [pure_site_install] Error 17
  /usr/bin/make install  -- NOT OK


I have no idea how to correct this. Any suggestions? I tried applying alien to a GTK2-sexy RPM package I found via Google, but that didn't work, either.

---

### Post by F-3582 on 2008-01-01
Wanna know a really cool way of installing it?

All you need is dh-make-perl and libsexy-dev. Now do this:

```
sudo dh-make-perl --build --cpan Gtk2::Sexy
sudo dpkg -i libgtk2-sexy-perl_0.02-1_i386.deb
```

Afterwards you'll probably need to restart Checkgmail and that's it.

---

### Post by Greg T. on 2008-01-01
It installed! Thanks. 

Curiously, when I click on a message link in a checkgmail popup box it gives me a 404 error, but when I click on the "Open" link beneath it, Gmail opens the message.

[EDIT: I checked out the SVN version and this appears to be fixed, more or less.]

---

### Post by jdarias on 2008-01-01
Can somebody please post a compiled package?
When i try to install dh-make-perl and libsexy-dev i get a ton of packages to get installed...
Would be of great help...

---

### Post by F-3582 on 2008-01-01
> **jdarias said:**
> Can somebody please post a compiled package?
When i try to install dh-make-perl and libsexy-dev i get a ton of packages to get installed...
Would be of great help...

Here you go.

---

### Post by jdarias on 2008-01-01
Thank you so much!!
It worked flawlessly! Now i see the nifty blue linkies that open in firefox as i click them...
I'm sure many people will benefit! 
here's a song for you!
:guitar:

---

### Post by hebetude on 2008-02-02
Id thank you twice on this thread if I could.  One for the cool dh-make-perl command and 2 for making it when that command kept failing on me:
```

Can't locate ExtUtils/Depends.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at Makefile.PL line 9.
BEGIN failed--compilation aborted at Makefile.PL line 9.
make: *** [build-stamp] Error 2

```

Looks like it downloaded some files alright, but failed to build them.  I'll try your deb thanks

---

### Post by puccaso on 2008-02-08
ok i sorted that

but i use /'s in my labels
it dies when labels are written with /

any work arounds?

---

### Post by F-3582 on 2008-02-09
You might wanna file a [bug]("http://sourceforge.net/tracker/?group_id=137480&atid=738663").

---

### Post by OdeAd on 2008-05-22
> **hebetude said:**
> Id thank you twice on this thread if I could.  One for the cool dh-make-perl command and 2 for making it when that command kept failing on me:
```

Can't locate ExtUtils/Depends.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at Makefile.PL line 9.
BEGIN failed--compilation aborted at Makefile.PL line 9.
make: *** [build-stamp] Error 2

```

Looks like it downloaded some files alright, but failed to build them.  I'll try your deb thanks

I dont know perl or CPAN very well ,but this how I solved it in my PC.
the "Can't locate " stuff tells you its some kind a dependency issue.
look in  ~/.cpan/build/Gtk2-Sexy-0.02/Makefile.PL ,at line 9(and 10 and 111) there 3 use statements :
```
use ExtUtils::Depends;
use ExtUtils::PkgConfig;
use ExtUtils::MakeMaker;

```

Install the these modules manually :```
sudo perl -MCPAN -e 'install  ExtUtils::Depends'
```repeat the process for the use statement on line 10 (11?) ,and then try to install Gtk2::Sexy again:
```
perl -MCPAN -e 'install  Gtk2::Sexy'
```
Now you can enjoy link goodness in checkgmail ...

Oded

---

### Post by olskar on 2008-05-22
Does anyone else than me suffer from very slow startuptime and high CPU when starting the program? Using ubuntu 8.04..

---

### Post by karldiechmann on 2008-05-24
My checkgmail doesn't work.
```

karldickman@karldickman-laptop:~$ checkgmail -v
CheckGmail v1.12.1svn
Copyright Â© 2005-7 Owen Marshall

:15: parser error : error parsing attribute name
               [new label]="300" />
               ^
:15: parser error : attributes construct error
               [new label]="300" />
               ^
:15: parser error : Couldn't find end of Start Tag label_delay line 14
               [new label]="300" />
               ^ at /usr/lib/perl5/XML/LibXML/SAX/Parser.pm line 31
A thread exited while 2 threads were running.

```

---

### Post by djkmmo on 2008-06-18
> **karldiechmann said:**
> My checkgmail doesn't work.
```

karldickman@karldickman-laptop:~$ checkgmail -v
CheckGmail v1.12.1svn
Copyright Â© 2005-7 Owen Marshall

:15: parser error : error parsing attribute name
               [new label]="300" />
               ^
:15: parser error : attributes construct error
               [new label]="300" />
               ^
:15: parser error : Couldn't find end of Start Tag label_delay line 14
               [new label]="300" />
               ^ at /usr/lib/perl5/XML/LibXML/SAX/Parser.pm line 31
A thread exited while 2 threads were running.

```

I have a similar problem:

```
error parsing attribute name
attributes construct error
xmlParseStartTag: problem parsing attributes
Couldn't find end of Start Tag label_delay line 14 at /usr/lib/perl5/XML/LibXML/SAX.pm line 64
 at /usr/share/perl5/XML/Simple.pm line 370
A thread exited while 2 threads were running.
```

Anyone out there who can help?

---

### Post by josh2020 on 2008-07-22
> **djkmmo said:**
> I have a similar problem:

```
error parsing attribute name
attributes construct error
xmlParseStartTag: problem parsing attributes
Couldn't find end of Start Tag label_delay line 14 at /usr/lib/perl5/XML/LibXML/SAX.pm line 64
 at /usr/share/perl5/XML/Simple.pm line 370
A thread exited while 2 threads were running.
```

Anyone out there who can help?


See this post [http://www.backports.ubuntuforums.org/showthread.php?t=732135](http://www.backports.ubuntuforums.org/showthread.php?t=732135)

I had errors in the same places as you're having. My problem was a label name with a space e.g. "ABC email". This caused 

[INDENT]Specification mandate value for attribute ABC
attributes construct error at /usr/lib/perl5/XML/LibXML/SAX.pm line 64
 at /usr/share/perl5/XML/Simple.pm line 370
A thread exited while 2 threads were running.[/INDENT]

My problem was resolved by replacing the space between ABC and email with a dash and saving the file. No idea whether my label check is working now, but checkgmail is working fine otherwise.

I suspect your problem can be found in your ~/.checkgmail/pref.xml file. Based on your error I expect you'll find a special character (<>?\") in your label_delay tag. Make your label name standard characters without spaces and see if that solves your problem.

Good luck.

---

### Post by hotweiss on 2008-10-15
> **F-3582 said:**
> Here you go.

Thanks that did the trick in 1.13.

---

### Post by MyR on 2008-11-07
Is there an easy way to install libgtk2-sexy on ubuntu 8.10 intrepid?

---

### Post by hyperair on 2008-11-07
I've uploaded it to my PPA ([http://launchpad.net/~hyperair/+archive](http://launchpad.net/~hyperair/+archive)) so grab the deb from there and install it when it's done building.

---

### Post by juanbretti on 2008-11-23
Or just do:
```
sudo aptitude install checkgmail
``` and that's it!

---

### Post by MyR on 2008-11-23
> **pepemosca said:**
> Or just do:
sudo aptitude install checkgmail
and that's it!

nope. checkgmail does not depend on libgtk2-sexy and furthermore libgtk2-sexy is not in the repositories.
peace

---

### Post by juanbretti on 2008-11-23
> **MyR said:**
> nope. checkgmail does not depend on libgtk2-sexy and furthermore libgtk2-sexy is not in the repositories.
peace

I don't get it... I saw those dependencies on the install!?!?
Did you try with "aptitude" or "apt-get"?

As you can see, I'm a newbee... so, maybe I'm doing something extra I can't tell.


The truth, is that I got it installed, but is not working because always says: "Error 401, error in loging" or something like that

---

### Post by juanbretti on 2008-11-23
BTW, does anyone knows where does the CheckGmail saves it's preferences?
Where is that file!?

Thanks!

---

### Post by MyR on 2008-11-23
> **pepemosca said:**
> BTW, does anyone knows where does the CheckGmail saves it's preferences?
Where is that file!?

Thanks!

in ~/.checkgmail

---

### Post by juanbretti on 2008-11-23
Sorry, completely new here:

Should I type in terminal: sudo gedit ~/.checkgmail?

Where is "~"?
What the "." means?

Sorry.
And thanks for your reply.

---

### Post by juanbretti on 2008-11-23
Ok, is a directory.

So, the ~ : is like /home/username?
And the . : is a "hidden" folder?

---

### Post by MyR on 2008-11-23
> **pepemosca said:**
> Ok, is a directory.

But, what the . and ~ means?
~ is your home directory, the same as /home/pepemosca or whatever your username is. 
~/ is *inside* your home directory
.checkgmail is the folder checkgmail uses to store its settings; the "." in front makes it hidden. in nautilus (the file browser) you can view hidden folders/files by hitting ctrl+h
why did you need to know where the file was located?
peace

---

### Post by juanbretti on 2008-11-24
> **MyR said:**
> ~ is your home directory, the same as /home/pepemosca or whatever your username is. 
~/ is *inside* your home directory
.checkgmail is the folder checkgmail uses to store its settings; the "." in front makes it hidden. in nautilus (the file browser) you can view hidden folders/files by hitting ctrl+h
why did you need to know where the file was located?
peace


I wanted to delete the pref file and start all over again.

Oh, thanks for the lesson :)

---

