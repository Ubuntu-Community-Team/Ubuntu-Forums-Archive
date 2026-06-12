---
title: "[Howto] Use Mutt with Gmail"
date: 2008-12-25
forum: Tutorials
---

### Post by andrew.46 on 2008-12-25
This guide has been converted to a wiki:

[https://help.ubuntu.com/community/MuttAndGmail](https://help.ubuntu.com/community/MuttAndGmail)

but help is still available via this Forum thread :)

---

### Post by hyper7 on 2008-12-26
I'm unable to find msmtp in my Intrepid respositories.

---

### Post by andrew.46 on 2008-12-26
Hi hyper7,

> **hyper7 said:**
> I'm unable to find msmtp in my Intrepid respositories.

msmtp is available in the Universe Repository. Details of the package can be seen [here]("http://packages.ubuntu.com/intrepid/mail/msmtp"). To add the Universe Repository you will need to go System ----> Administration ----> Software Sources. When you are there ensure there is a tick against 'Community-maintained Open Source software (universe)' box. Then press 'Close' and your sources database should be reloaded and you can then download msmtp.

Hope this helps,

Andrew

---

### Post by Nxion on 2008-12-27
Thank you very much for this guide. It worked wonderfully and I am in love with it. The only think I am having issue with is the colours. I use a transparent terminal and a black background. Ill have to tweak it :) But thanks again! Its is awesome

---

### Post by andrew.46 on 2008-12-27
Hi Nxion,

Thanks for the feedback!

> **Nxion said:**
> Thank you very much for this guide. It worked wonderfully and I am in love with it. The only think I am having issue with is the colours. I use a transparent terminal and a black background. Ill have to tweak it :) But thanks again! Its is awesome

I do not use a black background or my terminal but some use the following colors for such a scheme:

```

#---- Mutt Colors for Black Background -------
#color   object     foreground       background
color   hdrdefault   blue              black
color   quoted       blue              black
color   signature    blue              black
color   attachment   red               black
color   message      brightred         black
color   error        brightred         black
color   indicator    black             red
color   status       brightgreen       blue
color   tree         white             black
color   normal       white             black
color   markers      red               black
color   search       white             black
color   tilde        brightmagenta     black
color   index        blue              black ~F
color   index        red               black "~N|~O"
```

And I include a little 'key' to show how the basic colors are plotted out.

All the best,

Andrew

---

### Post by Nxion on 2008-12-28
> **andrew.46 said:**
> Hi Nxion,

Thanks for the feedback!



I do not use a black background or my terminal but some use the following colors for such a scheme:

```

#---- Mutt Colors for Black Background -------
#color   object     foreground       background
color   hdrdefault   blue              black
color   quoted       blue              black
color   signature    blue              black
color   attachment   red               black
color   message      brightred         black
color   error        brightred         black
color   indicator    black             red
color   status       brightgreen       blue
color   tree         white             black
color   normal       white             black
color   markers      red               black
color   search       white             black
color   tilde        brightmagenta     black
color   index        blue              black ~F
color   index        red               black "~N|~O"
```And I include a little 'key' to show how the basic colors are plotted out.

All the best,

Andrew

Thanks man!.  works like a charm!

---

### Post by pajoohesh on 2008-12-29
[COLOR="Blue"]Thanks andrew for the nice tutorial. :D

There is an issue about entering [COLOR="Red"]Gmail password[/COLOR]:( which is not so secure specially in a multi-user platform. is it possible not to insert the password in those files, instead one enters it once wants to check mail at the terminal?[/COLOR]

---

### Post by andrew.46 on 2008-12-29
Hi pajoohesh,

Thanks for your feedback:

> **pajoohesh said:**
> There is an issue about entering [COLOR="Red"]Gmail password[/COLOR]:( which is not so secure specially in a multi-user platform. is it possible not to insert the password in those files, instead one enters it once wants to check mail at the terminal?

The 2 files that contain the passwords are $HOME/.fetchmailrc and $HOME/.msmtprc. Both of these files are set to 0600 which I will admit is not the robust protection but may suffice for many.

However if you wish simply omit the password line in the .fetchmailrc file:

```
there with password '**[COLOR="Red"]Gmail Password[/COLOR]**' # Your Gmail Password 
``` 

and fetchmail will prompt you for a password before proceding. However I don't believe that this is possible with msmtp because when mutt calls msmtp there is no mechanism for msmtp to ask for password before proceding. I believe this is possible *directly* from the commandline using msmtp but not via mutt.

Not sure how to get around this one?

Andrew

---

### Post by pajoohesh on 2008-12-29
[COLOR="Blue"]Hi Andrew,

Thanks for the answer. I am new to linux and do not know much about mutt. Should I use the msmtp *directly*, Will I lose the benefits of using mutt. I have found this in msmtp manual:[COLOR="Sienna"]> `password [secret]'
Set your password for SMTP authentication. An empty argument unsets the password. Authentication must be activated with the `auth' command. If no password is set but one is needed during authentication, msmtp will try to find it in ~/.netrc. If that fails, it will try to find it in SYSCONFDIR/netrc (use --version to find out what SYSCONFDIR is on your platform). If that fails, it will try to get it from a system specific keychain (if available). If that fails but a controlling terminal is available, msmtp will prompt you for it.[/COLOR]if mutt is not using a terminal what about the other methods that it tries to find password. 

I want to find a way not to put the password just naked in a file.[/COLOR]

---

### Post by andrew.46 on 2008-12-29
Hi pajoohesh,

Thanks again for your feedback:

> **pajoohesh said:**
> Thanks for the answer. I am new to linux and do not know much about mutt. Should I use the msmtp *directly*, Will I lose the benefits of using mutt. I have found this in msmtp manual:[COLOR="Sienna"][/COLOR]if mutt is not using a terminal what about the other methods that it tries to find password. 

I experimented with these methods and unfortunately could not get them to work as you have mentioned using mutt.

> I want to find a way not to put the password just naked in a file.

Perfectly understandable. Bear in mind that the setting of 0600 actually means that only yourself and root can read and alter this file, so the password is not *completely* exposed. However I have noticed that Version 1.4.17 of msmtp was released only recently and this version has support for the Gnome keyring. Details can be seen in [the changelog]("http://msmtp.cvs.sourceforge.net/*checkout*/msmtp/msmtp/ChangeLog").

I had a quick look at the source for 1.4.17 and saw the new option:

```
./configure --with-gnome-keyring 
```

which is exactly what you are after :-). However this is a very new version, only 2 or 3 days old, and not available even in the upcoming Jaunty Jackalope yet and it is beyond the scope of this guide to demonstrate how to compile this one.

You may very well be better off to wait for a decent debiam package of the new msmtp to be released and then hide your password in the keychain. Sorry for not having a better answer :(.

All the best,

Andrew

---

### Post by pajoohesh on 2008-12-29
> **andrew.46 said:**
> Hi pajoohesh,
Thanks again for your feedback:

I experimented with these methods and unfortunately could not ...


Perfectly understandable. Bear in mind that the setting of 0600 actually means that only yourself and root can read and alter this file, so the password is not *completely* exposed....

All the best,

Andrew


[COLOR="Blue"]Thanks for your kind help. I really appreciate it.:)[/COLOR]

---

### Post by enoughsaid05 on 2008-12-30
Hihi

Got a question here. If I have emails from multiple accounts how do I go about receiving emails using mutt. Do I simply add in the necessary configuration for various email accounts all in one fetchmailrc file? Thanks!

---

### Post by andrew.46 on 2008-12-30
Hi enoughsaid:

> **enoughsaid05 said:**
> Got a question here. If I have emails from multiple accounts how do I go about receiving emails using mutt. Do I simply add in the necessary configuration for various email accounts all in one fetchmailrc file? Thanks!

I should say straight up that I have not actually done this but it looks reasonably straightforward. Fetchmail works with multiple accounts and each is simply listed after the other in the .fetchmailrc. From the man pages:

> Multiple servers may be listed:

         poll pop.provider.net proto pop3 user "jsmith" pass "secret1"
         poll other.provider.net proto pop2 user "John.Smith" pass "My^Hat"

I would suspect that you might want to sort these mails a little with procmail and perhaps deliver to seperate folders?

The msmtp html help pages have a nice section on using multiple accounts that should be helpful as well:

[http://msmtp.sourceforge.net/doc/msmtp.html#Using-msmtp-with-Mutt](http://msmtp.sourceforge.net/doc/msmtp.html#Using-msmtp-with-Mutt)

This should get you started but I will admit I have never tried these techniques myself.

All the very best,

Andrew

---

### Post by Durrock on 2009-02-02
I set this up and it works great. However, it only seems to get mail up to a year ago (or so). Never my "newest" mail. 

Also - it seems to download the copious amounts of spam my gmail account receives.  I thought that would be filtered off on gmails servers?

---

### Post by andrew.46 on 2009-02-03
Hi Durrock,

> **Durrock said:**
> I set this up and it works great. However, it only seems to get mail up to a year ago (or so). Never my "newest" mail. 

This is one of the annoying 'features' of Gmail where the server only permits a certain number of email messages to be downloaded at a time. Try using 'nokeep' instead of 'keep' and run fetchnews a few times.

> Also - it seems to download the copious amounts of spam my gmail account receives.  I thought that would be filtered off on gmails servers?

This should not be happening unless the spam is sitting in your inbox? Have a look via the web interface and make sure your filters are in place and moving / deleting the spam.

All the best,

Andrew

---

### Post by jackietreehorn on 2009-02-03
Thanks for making this excellent guide, but I ran into a problem...which I eventually fixed. Thanks again for the excellent guide.

---

### Post by BIGtrouble77 on 2009-02-03
Thanks for the howto.  Works well with my Google Apps account. 

-bt

---

### Post by andrew.46 on 2009-02-03
Hi jackietreehorn,

> **jackietreehorn said:**
> Thanks for making this excellent guide, but I ran into a problem...which I eventually fixed. Thanks again for the excellent guide.

Always happy to get someone started off with mutt :-).

Andrew

---

### Post by Durrock on 2009-02-05
> **andrew.46 said:**
> Hi Durrock,



This is one of the annoying 'features' of Gmail where the server only permits a certain number of email messages to be downloaded at a time. Try using 'nokeep' instead of 'keep' and run fetchnews a few times.




Doesn't that delete all the messages on the gmail side though?  What if I want to keep the messages there for archival?

---

### Post by andrew.46 on 2009-02-05
Hi Durrock,

> **Durrock said:**
> Doesn't that delete all the messages on the gmail side though?  What if I want to keep the messages there for archival?

Well it *should* but this is in fact controlled by a setting in Gmail:

Settings --> Forwarding and POP/IMAP --> POP Download --> When messages are accessed with POP:

And in your case I guess you would choose: 'Archive Gmail's copy'.

Andrew

---

### Post by fluxerj on 2009-02-06
#

As the writer of the first site you discussed I would like to make a brief defence :-)

1. When you say ‘it does too much unnecessary stuff using too many unnecessary programs’, this is the traditional way in Linux. i.e. One program to download, one program to filter, one program to read etc. Having said that now that IMAP has arrived at Gmail there is obviously a new way to do this, for Gmail at least.

---

### Post by andrew.46 on 2009-02-06
Hi fluxerj,

> **fluxerj said:**
> As the writer of the first site you discussed I would like to make a brief defence :-)

1. When you say ‘it does too much unnecessary stuff using too many unnecessary programs’, this is the traditional way in Linux. i.e. One program to download, one program to filter, one program to read etc. Having said that now that IMAP has arrived at Gmail there is obviously a new way to do this, for Gmail at least.

I remember that exchange, and of course you have quoted my words :-). I experimented with IMAP / mutt / gmail and I did not like it at all although I believe that many do. Perhaps I have become a little old fashioned....

Andrew

---

### Post by Girya on 2009-02-06
Thanks Andrew46. your howto worked flawlessly.

I made one addition to my .muttrc file that others might like:

> #=====================================================#
# split pager screen
set pager_index_lines=10

this addition splits the pager so that you can read your mail and see your mail headers inthe same screen. see the attachment for a screenshot  


I don't suppose you know of any good procmail tutorials?

kevin

---

### Post by andrew.46 on 2009-02-06
Hi Girya,

> **Girya said:**
> 
```
# split pager screen
set pager_index_lines=10 
```

this addition splits the pager so that you can read your mail and see your mail headers inthe same screen. see the attachment for a screenshot  


Looks good and makes mutt look even more like my favourite news reader slrn :-). I will admit that I have never heard of this setting before.

> I don't suppose you know of any good procmail tutorials?

I have to admit that I am no procmail guru and I suspect not many people are. A good starting point is here:

Procmail FAQ
[http://partmaps.org/era/procmail/mini-faq.html](http://partmaps.org/era/procmail/mini-faq.html)

All the best,

Andrew

---

### Post by skankster on 2009-02-13
> **Girya said:**
> 

I don't suppose you know of any good procmail tutorials?

kevin

[http://www.ii.com/internet/robots/procmail/qs/](http://www.ii.com/internet/robots/procmail/qs/)

---

### Post by FakeOutdoorsman on 2009-02-14
> **Girya said:**
> I don't suppose you know of any good procmail tutorials?
Not a tutorial, but I've used txt2regex to help me get around those regular expressions in procmail.  Might just be me, but they aren't exactly easy.  You can also specify procmail syntax in txt2regex.

---

### Post by sylecn on 2009-02-15
Hi Andrew,
  Thanks for posting such great and detailed guide. It is very helpful to me.

  I have a quick question, I noticed that exim4 and a few related pkg is installed when I'm following this how-to. Is exim4 required for the whole thing to work correctly? Does it have the same function as msmtp? I'm a completely newbie on mail server. I didn't config exim4 myself. 

  I also want to ask why mutt put mail text into Attachments by default. How can I change that behavior?

---

### Post by andrew.46 on 2009-02-16
Hi sylecn,

> **sylecn said:**
> I have a quick question, I noticed that exim4 and a few related pkg is installed when I'm following this how-to. Is exim4 required for the whole thing to work correctly? Does it have the same function as msmtp? I'm a completely newbie on mail server. I didn't config exim4 myself. 

Unfortunately installation of mutt from the Ubuntu repository is tied to the installation of exim, this is how the Debian package has been put together. You can safely ignore exim however unless you are keen to use it, my advice is t simply use msmtp.

> I also want to ask why mutt put mail text into Attachments by default. How can I change that behavior?

Do you mean that when you select 'View' for attachments you see a page full of text? If this is the case you need to configure your mailcap entries or probably simpler set an easier path to 'save' attachments.

A neat addition to .muttrc to allow default save to your desktop is:

```
macro attach s "<save-entry><bol>$HOME/Desktop/<eol>"
```

There are many ways to set up mailcap, I prefer to give mutt its own by sourcing it from .muttrc. The following example shows how to use w3m to automatically view html enriched mail:

```
set mailcap_path="~/mail/mutt/mutt_mailcap"
auto_view text/html                             
set implicit_autoview=yes
``` 

and in the file mutt_mailcap

```
text/html; /usr/bin/w3m -cols 90 -dump -T text/html '%s'; copiousoutput
```

You will of course need to install w3m :-).

Andrew

---

### Post by sylecn on 2009-02-16
Hi Andrew,
Thanks to your reply. The second question is when I send a mail via mutt, it treats the text as inline attachment. This is not a problem when viewing the mail in Gmail or Mutt, but when using yahoo web mail, it's ugly.
Here is the screenshot before sending mail in mutt:
[[IMG]http://img25.imageshack.us/img25/4075/mutttextasattachment1lx6.th.jpg[/IMG]](http://img25.imageshack.us/my.php?image=mutttextasattachment1lx6.jpg)
Here is the yahoo mail when reading the mail online:
[[IMG]http://img9.imageshack.us/img9/7301/mutttextasattachment2hb4.th.jpg[/IMG]](http://img9.imageshack.us/my.php?image=mutttextasattachment2hb4.jpg)

---

### Post by andrew.46 on 2009-02-17
Hi,

The screen that shows mutt about to send an email is completely normal, this is as it is seen on my own system. Unfortunately I am not familiar with yahoo mail, could there be a problem at that end?

Andrew

---

### Post by Lutherian on 2009-03-21
Andrew, despite many tutorials on setting up mutt + gmail, yours is the best presented in terms of methodical layout - which comforts newcomers to mutt.

My limitations being what they are, I was still unsuccessful in my attempts.

Following the instructions verbatim, I run the command "fetchmail -v" from within the mutt shell, and the console show a successful log-in to gmail, thereafter I see line-after line of asterisks *****.*****.******.*****.

Eventually, I press control-c and exit the shell, returning to mutt.
The mail box still shows 0 e-mails.

When looking at /var/spool/mail/myusername - I see that the file is empty.

Could this be a fault in my .fetchmailrc or .procmailrc configuration files?

Has anyone else experienced this dilemma?

Thanks to all for assistance

---

### Post by andrew.46 on 2009-03-21
Hi Lutherian,

> **Lutherian said:**
> Following the instructions verbatim, I run the command "fetchmail -v" from within the mutt shell, and the console show a successful log-in to gmail, thereafter I see line-after line of asterisks *****.*****.******.*****.

Eventually, I press control-c and exit the shell, returning to mutt.
The mail box still shows 0 e-mails.


Always good to see a new mutt user :-). There is an excellent possibility that your setup is fine as the lines of asterisks you see are what fetchmail shows when downloading a long email or more likely a big attachment. I would suggest either letting the process run ( make yourself a cup of tea) or log on via the web interface and deal with the big email there.

All the very best,

Andrew

---

### Post by Lutherian on 2009-03-23
Hi Andrew. [Status Update]

I (eventually) had success (see screenshot) - I've learned some things along the way that may be useful for newbies and sensei's / teachers like yourself.

(1) False Assumption. In reading your tutorial, where "username" appeared, I automatically assumed you were referring to the G-Mail username, whilst infact you were referring to the Linux Logon Username, unless you specifically mentioned gmail-username.

This obviously is **not** a flaw in the tutorial, but it shows the danger of the "quick-fix, cut-and-paste" method of which I'm so guilty. After 2 years of using Ubutnu almost exclusively at home, I'm still guilty of thinking in a Windows OS frame of mind.

I happy to say that on the (long) detour I've learn all sorts of things about fetchmail (you can limit the size of individual e-mail downloads etc, etc)

The lessons learned are:

Learners:
*Understand* the system as a whole - don't think in compartments.
Learn the linux _fundamentals_ (file systems, permissions, system structure, user accounts etc) i.e. Read More!

Teachers:
If possible, give us hints about the broader picture - some of us need it :D

I'll now turn my attention to reading the texts on how to use mutt properly.

Once again, thanks.

---

### Post by andrew.46 on 2009-03-24
Hi Lutherian,

Glad to hear you made it :-). The confusion with usernames has needed changing for a while, I have corrected it on [this page's big brother]("http://www.andrews-corner.org/mutt.html") but until now I have not altered this particular guide. On my next days off I will make it all a little clearer.

As for 'sensei / teacher' I have some bad news for you: I am just another Linux user who has done a little research in one small corner of the Linux world :-).

All the best,

Andrew

---

### Post by andrew.46 on 2009-03-25
Hi,

I have altered the guide to hopefully make the different usernames and passwords a little clearer by pirating the idea from my website :-). ANybody has trouble with the new setup just drop me a line.

All the best,

Andrew

---

### Post by azbot on 2009-03-27
Hi Andrew

Thank you for this information, I have tried a number of times to get Mutt to work without success and thanks to this thread it finally is. I did have some trouble getting it all to work and learned more along the way.

The main problem I came across was to do with the ~/Mail/certs/ folder. On the 'this pages big brother' page you cover creating the specific certificates and placing them in the users 'certs' folder using the perl script etc. On this thread as I understand this is not necessary as a general certificte file is pointed to.

I am unclear about this, my set-up from this thread did not work and fetchmail reported a certificate error. I solved it by creating the files as suggested on the other site and it works now. I would like to understand why this happened though and would appreciate any thoughts you have on the matter.

It is my first time with Mutt and I'm enjoying it immensely along with screen, irssi, elinks and rtorrent all of which keep me where my fascination is: the command line.

Thanks again.

---

### Post by andrew.46 on 2009-03-28
Hi azbot,

> **azbot said:**
> 

Thank you for this information, I have tried a number of times to get Mutt to work without success and thanks to this thread it finally is. I did have some trouble getting it all to work and learned more along the way.


Glad it all worked for you! Of course this small guide is just a beginning to using mutt, but I hope a good solid beginning nevertheless.

> The main problem I came across was to do with the ~/Mail/certs/ folder. On the 'this pages big brother' page you cover creating the specific certificates and placing them in the users 'certs' folder using the perl script etc. On this thread as I understand this is not necessary as a general certificte file is pointed to.

I personally think the perl script that assembles the certificates is the coolest thing I have seen for a long time :-).

> I am unclear about this, my set-up from this thread did not work and fetchmail reported a certificate error. I solved it by creating the files as suggested on the other site and it works now. I would like to understand why this happened though and would appreciate any thoughts you have on the matter.

Looks like I have made an error in the directory path in the ~/.fetchmailrc for which I apologise. This crept in with a copy and paste change of this guide from information on my website. I have altered the ~/.fetchmailrc to the correct settings now. Apologies again.

> It is my first time with Mutt and I'm enjoying it immensely along with screen, irssi, elinks and rtorrent all of which keep me where my fascination is: the command line.

Well perhaps you would enjoy mutt's twin brother slrn? This is my main interest to tell the truth and Usenet is still a busy place no matter what people seem to think. Guide here:

[Howto] Setup the commandline newsreader slrn
[http://ubuntuforums.org/showthread.php?p=2852968](http://ubuntuforums.org/showthread.php?p=2852968)

Perhaps I will see you on alt.os.linux.ubuntu?

All the very best,

Andrew

---

### Post by Roobert on 2009-05-01
Hi Andrew,

Thanks for the guide! It is very well written and easy to follow. 

I've run into a problem, however. After following all of your steps, I get the error "Pop host is not defined" when trying to download mail by typing 'G' in Mutt. 

I thought the pop host was clearly defined in my ~/.fetchmailrc:

```
poll pop.gmail.com                   
with proto POP3                      
user 'thepattonian@gmail.com'
there with password 'my password'
is 'epatton' here
mda "/usr/bin/procmail -d %T"
options                                                             
no keep                                 
ssl                                  
sslcertck                            
sslcertpath /etc/ssl/certs
```My username on this Linux box is epatton. Any ideas on where I screwed up? 

~ Eric.

---

### Post by andrew.46 on 2009-05-01
Hi Eric,

> **Roobert said:**
> 
I've run into a problem, however. After following all of your steps, I get the error "Pop host is not defined" when trying to download mail by typing 'G' in Mutt. 

Well, your .fetchmailrc looks ok. I am a little puzzled by the 'G' key. have you simply redefined the macro I gave:

```
macro index,pager I '<shell-escape> fetchmail -v<enter>'
```

which of course uses the 'I' key? If there is a problem with this macro the 'standard' way is to press the '!' key while mutt is open and then run 'fetchmail -vv' at the prompt.

Please get back to me if this is not the actual problem.

Andrew

---

### Post by Roobert on 2009-05-02
> **andrew.46 said:**
> Hi Eric,



Well, your .fetchmailrc looks ok. I am a little puzzled by the 'G' key. have you simply redefined the macro I gave:

```
macro index,pager I '<shell-escape> fetchmail -v<enter>'
```

which of course uses the 'I' key? If there is a problem with this macro the 'standard' way is to press the '!' key while mutt is open and then run 'fetchmail -vv' at the prompt.

Please get back to me if this is not the actual problem.

Andrew

You know what? It was my own mistake - I didn't have the macro inserted in .muttrc for some reason. I'm up and running with Mutt now, and loving it!! Thanks so much,

Cheers,

~ Eric.

---

### Post by passonno on 2009-05-02
Hi,

So, I believe that I have followed your instructions exactly, but am still showing an empty mailbox, and mutt shows no messages.

Can you help me figure this out?

---

### Post by andrew.46 on 2009-05-03
Hi passonno,

> **passonno said:**
> So, I believe that I have followed your instructions exactly, but am still showing an empty mailbox, and mutt shows no messages.

There are a couple of things to check:

[LIST=1]
[*]Does your ~/.fetchmailrc contain the line:
```
mda "/usr/bin/procmail -d %T" 
```
[*]Can also tell me the results of the following:
```
echo $MAIL
```
[*]Can you also tell me what you have set in your ~/.muttrc for:
```
# If not set in environment variables:
set spoolfile = 
```
[/LIST]

There may be a break in the required sequence of: Fetchmail gets the mail ----> Delivers it to Procmail -----> Sends it to the Mail Spool ------> Mutt reads the spool. Once this is correctly set you will have no problems :-).

All the best,

Andrew

---

### Post by passonno on 2009-05-03
Step 1 is Yes
Step 2 is /var/spool/mail/passonno (gmail username) local username is anthony
Step 3 is /var/spool/mail/anthony 

I don't remember exactly what I did(work injury , lots of vicodin for pain) but I believe I "kinda" fixed it by pointing it to /var/spool/mail/username, when I noticed no mailbox was even created.

Is that a good idea?  

It works now, but I don't like the idea of cluttering up the root filesystem where it should be in ~/.  Could I solve this by using a symbolic link?

---

### Post by andrew.46 on 2009-05-03
Hi passonno,

> **passonno said:**
> Step 1 is Yes
Step 2 is /var/spool/mail/passonno (gmail username) local username is anthony
Step 3 is /var/spool/mail/anthony 

Can I suggest that you alter the setting in ~/.bashrc to the following:

```

# Sets the Mail Environment Variable
MAIL=/var/spool/mail/anthony && export MAIL

```

This will use your *system* username rather then your *Gmail* username, this is the more correct method. If this is done correctly mutt will read this variable and the 'set spoolfile' setting in ~/.muttrc becomes redundant.

> I don't remember exactly what I did(work injury , lots of vicodin for pain) but I believe I "kinda" fixed it by pointing it to /var/spool/mail/username, when I noticed no mailbox was even created. Is that a good idea?  It works now, but I don't like the idea of cluttering up the root filesystem where it should be in ~/.  Could I solve this by using a symbolic link?

The way I have set the guide is the 'traditional' method where incoming mail is delivered to the system mail spool *first* and I personally think that you would be better to keep it this way.

However you can require that Mutt moves all mail to your local mailbox by altering the setting I have given in the sample ~/.muttrc from:

```
set move=no   # Don't move mail from the spool.
```

to:

```
set move=yes    # Move mail from the spool to the local mailbox on closing.
```

and this will move *all* the mail that has not already been sorted by procmail recipes from /var/spool/mail/anthony to ~/Mail when you close mutt. There really are many, many different ways of doing this and I will admit that this guide shows the most conservative technique :-).

All the best,

Andrew

---

### Post by bollix47 on 2009-05-14
I too would like to extend my gratitude to Andrew for this guide.

I am now easily able to have my remote computers automatically send an e-mail to my home computer describing their current folding@home status every hour which for me is quite handy as it will indicate whether there are problems at the remote location.

Thanks very much. :D

---

### Post by andrew.46 on 2009-05-14
Hi bollix47,

> **bollix47 said:**
> I too would like to extend my gratitude to Andrew for this guide.

Thank you for your kind words,

Andrew

---

### Post by PendragonUK on 2009-05-15
Before sending people (novices) on this little journey, you might want to remember that VIM isn't the easiest of editors and is not installed by default.

It took around 5 minuets to google for instructions on VIM usage and a fare amount of button mashing to get the file to save and then VIM to exit.

Thanks for my little adventure...

---

### Post by andrew.46 on 2009-05-15
Hi PenfragonUK,

> **PendragonUK said:**
> Before sending people (novices) on this little journey, you might want to remember that VIM isn't the easiest of editors and is not installed by default.

It took around 5 minuets to google for instructions on VIM usage and a fare amount of button mashing to get the file to save and then VIM to exit.

My apologies for your first encounter with vim, I have been using it for so long now I had forgotten that it is not second nature to everybody :-). I shall update the guide with instructions to install vim and then run the vimtutor.

All the best,

Andrew

**Edit:** Corrections done, let me know if you feel this is a little better!

---

### Post by pizeta on 2009-05-15
Great guide!
Thank you so much :p

---

### Post by andrew.46 on 2009-05-15
Hi pizeta,

> **pizeta said:**
> Great guide!
Thank you so much :p

Thanks for your kind words! Good to see another mutt user in the making :-).

Andrew

---

### Post by ooolongT on 2009-05-18
> **PendragonUK said:**
> Before sending people (novices) on this little journey, you might want to remember that VIM isn't the easiest of editors and is not installed by default.

It took around 5 minuets to google for instructions on VIM usage and a fare amount of button mashing to get the file to save and then VIM to exit.

Thanks for my little adventure...

Just a quick note, I am very new to Mutt, and to Linux in general so I can understand the frustration with vim, but all I did was change that parameter in the .muttrc file.  My .muttrc file now reads: 

```

# which editor do you want to use? 
# vim of course!
# set editor="vim -c 'set tw=70 et' '+/^$' " 
# Actually, I decided to use Kate instead.  Will probably need some settings to get it to format correctly.
set editor="kate"
set edit_headers=yes      # See the headers when editing

```

I know my code is not as elegant as Andrew's (of course) but that does let me write my mails in Kate (I run Kubuntu).  Any input from anyone on how to improve this is welcome.  I hope this helps!

---

### Post by ooolongT on 2009-05-18
I am having trouble fetching my mail.

When I try to fetch the mail it looks like it is reading the Gmail server, but something is not right, here is what it says in the terminal, over and over again (of course the message is slightly different for different messages, but its complaint is the same)

```

reading message [COLOR="Red"]myusername[/COLOR]@gmail.com@gmail-pop.l.google.com:309 of 309 (10786 octets)
#*************************.*************************.*************************.****************.*****************.***************.****************.***************.************procmail: Suspicious rcfile "/home/[COLOR="Red"]user[/COLOR]/.procmailrc"
procmail: Couldn't read "/home/[COLOR="Red"]user[/COLOR]/.procmailrc"
 flushed
fetchmail: POP3> DELE 309
fetchmail: POP3< +OK marked for deletion
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Farewell.
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Mon 18 May 2009 02:26:40 PMPDT: poll completed
fetchmail: normal termination, status 0
Press any key to continue...

```

And when I hit a key, it goes right back into mutt, but no messages are displayed. 

Here is my .procmailrc file (although I just copied and pasted from this tutorial):
```
# Environment variable assignments
PATH=/bin:/usr/bin:/usr/local/bin 
VERBOSE=off                   # Turn on for verbose log
MAILDIR=$HOME/Mail            # Where Procmail recipes deliver
LOGFILE=$HOME/.procmaillog    # Keep a log for troubleshooting.

# Recipes
:0:
* ^TOmutt-user
mutt
```

I just double checked my Gmail account and it is set up for pop mail.
```
POP is enabled for all mail that has arrived since 4/23/06
```
Oddly, there seem to be a bunch of messages in /var/spool/mail/
.procmailrc is in the right folder, and the permissions are set right (I think)
```
-rwxrwxrwx  1 [COLOR="Red"]user   user[/COLOR]       287 2009-05-18 14:05 .procmailrc

```

Any idea why I am not seeing my emails?

---

### Post by bollix47 on 2009-05-18
```
reading message myusername@gmail.com@gmail-pop.l.google.com:309 of 309 (10786 octets)
#*************************.*************************.*************************.****************.*****************.***************.****************.***************.************procmail: Suspicious rcfile "/home/user/.procmailrc"
procmail: Couldn't read "/home/user/.procmailrc"

```

Check the .msmtprc and .fetchmailrc files in your home to ensure you've changed myusername and user with your personal info.

---

### Post by ooolongT on 2009-05-18
Bollix, thank you for your help.  It seems it was just a glitch.  I restarted and now it is retrieving my email.  However, I am still getting the error (I turrned off verbose this time as it appears it was not needed to view the error):

```

reading message [COLOR="Red"]myusername[/COLOR]@gmail.com@gmail-pop.l.google.com:43 of 322 (4002 octets)....procmail: Suspicious rcfile "/home/[COLOR="Red"]user[/COLOR]/.procmailrc"                                               
procmail: Couldn't read "/home/USER[COLOR="Red"][/COLOR]/.procmailrc"                                             
 flushed                                                                                   

```

Thanks to both you and Andrew!

---

### Post by andrew.46 on 2009-05-19
Hi ooolong,

> **ooolongT said:**
> However, I am still getting the error (I turrned off verbose this time as it appears it was not needed to view the error):

```

reading message [COLOR="Red"]myusername[/COLOR]@gmail.com@gmail-pop.l.google.com:43 of 322 (4002 octets)....procmail: Suspicious rcfile "/home/[COLOR="Red"]user[/COLOR]/.procmailrc"                                               
procmail: Couldn't read "/home/USER[COLOR="Red"][/COLOR]/.procmailrc"                                             
 flushed                                                                                   

```


The permissions on $HOME/.procmailrc are incorrect and hopefully once set correctly the error message will go. My own .procmailrc is set as follows:

```
andrew@skamandros~$ ls -l $HOME/.procmailrc
-rw-r--r-- 1 andrew users 574 2009-05-19 17:17 /home/andrew/.procmailrc
```

and to set these permission simply run:

```
chmod 0644 $HOME/.procmailrc
```

If this does not fix the issue could you post the results of:

```
ls -l $HOME/.procmailrc
```

again? But hopefully this will solve the problem :-).

All the best,

Andrew

---

### Post by ooolongT on 2009-05-19
Andrew, sorry for my delayed response.  I did get procmail working by changing the permissions. Thank you!

I am having a similar problem with GetLive.  Not sure what is going on, but I have started another thread about it [here]("http://ubuntuforums.org/showthread.php?p=7312478#post7312478").

---

### Post by andrew.46 on 2009-05-20
Hi ooolongT,

> **ooolongT said:**
> Andrew, sorry for my delayed response.  I did get procmail working by changing the permissions. Thank you!

Great news! I hope you enjoy the whole mutt experience, this little guide is very much 'only the tip of the iceberg' :-).

Andrew

---

### Post by qmemo on 2009-05-21
Hello, I came across this tut, I fully followed it, but I got an error, and can not figure out what's wrong ```

qmemo@some-where:~$ mutt
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Thu 21 May 2009 06:46:49 PM EEST: poll started
Trying to connect to 72.14.221.109/995...connected.
fetchmail: Issuer Organization: Equifax
fetchmail: Unknown Issuer CommonName
fetchmail: Server CommonName: pop.gmail.com
fetchmail: pop.gmail.com key fingerprint: 44:A8:E9:2C:FB:A9:7E:6D:F9:DB:F3:62:B2:9E:F1:A9
fetchmail: POP3< +OK Gpop ready for requests from 41.232.225.137 l19pf317553fgb.12
fetchmail: POP3> CAPA
fetchmail: POP3< +OK Capability list follows
fetchmail: POP3< USER
fetchmail: POP3< RESP-CODES
fetchmail: POP3< EXPIRE 0
fetchmail: POP3< LOGIN-DELAY 300
fetchmail: POP3< X-GOOGLE-VERHOEVEN
fetchmail: POP3< UIDL
fetchmail: POP3< .
fetchmail: POP3> USER exrs.2008@gmail.com
fetchmail: POP3< +OK send PASS
fetchmail: POP3> PASS *
fetchmail: POP3< +OK Welcome.
fetchmail: POP3> STAT
fetchmail: POP3< +OK 3 86884
fetchmail: POP3> LAST
fetchmail: POP3< -ERR Not supported
fetchmail: Not supported
fetchmail: POP3> UIDL
fetchmail: POP3< +OK
fetchmail: POP3< 1 GmailId1214bc1650fe0200
fetchmail: POP3< 2 GmailId12162d46bd760f01
fetchmail: POP3< 3 GmailId12163c410b329eff
fetchmail: POP3< .
3 messages for exrs.2008@gmail.com at pop.gmail.com (86884 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 740
fetchmail: POP3> TOP 1 99999999
fetchmail: POP3< +OK message follows
reading message exrs.2008@gmail.com@gmail-pop.l.google.com:1 of 3 (740 octets)
#*************procmail: Unknown user "exrs"
fetchmail: MDA returned nonzero status 67
 not flushed
fetchmail: POP3> LIST 2
fetchmail: POP3< +OK 2 83214
fetchmail: POP3> TOP 2 99999999
fetchmail: POP3< +OK message follows
reading message exrs.2008@gmail.com@gmail-pop.l.google.com:2 of 3 (83214 octets)
#**************************.**********************.***************************.************************************.**********************.*********************.********************.*********************.***********************.*******************.*********************.*******************.*********************.**********************.*************************.*****************************.**********************************.***************************.************************.*************************.****************************.***************************.*******************************.*****************************.*************************.******************************.***************************.***************************.***************************************.********************.************************.************************.*******************************.***************************.*******************************.*********************.**********************.**********************.*****************************.****************************.****************************.************************.******************************.*******************************.*******************.********************.*********************.***********************.*********************.*****************.********************.********************.****************************.**************************.**************************************.************************.****************************.**********************.********************.***********************.*********************.*********************.********************.******************************.*************************.*****************************************.************************.**************************************.******************************.*******************************.***************************.**********.***************************.*************************.****************************.***************************.************************.******************************.*******************.******************.**********************************.*****procmail: Unknown user "exrs"
fetchmail: MDA returned nonzero status 67
 not flushed
fetchmail: POP3> LIST 3
fetchmail: POP3< +OK 3 2930
fetchmail: POP3> TOP 3 99999999
fetchmail: POP3< +OK message follows
reading message exrs.2008@gmail.com@gmail-pop.l.google.com:3 of 3 (2930 octets)
#*********************************procmail: Unknown user "exrs"
fetchmail: MDA returned nonzero status 67
 not flushed
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Farewell.
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Thu 21 May 2009 06:47:00 PM EEST: poll completed
fetchmail: normal termination, status 0
Press any key to continue...

```

---

### Post by andrew.46 on 2009-05-21
Hi qmemo,

> **qmemo said:**
> 
```

#*************procmail: Unknown user "exrs"
fetchmail: MDA returned nonzero status 67

```

I will admit that I have never seen that error before :-). Can I ask that you post your entire $HOME/.fetchmailrc file, with the password masked of course. As well could you give the results of:

```
echo $USER
```

I have a suspicion that you may have an incorrect value for *user* in the .fetchmailrc file but just to cover all bases could you also post the contents of $HOME/.procmailrc?

All the best,

Andrew

---

### Post by qmemo on 2009-05-21
First of all thank you for replying me, here are the settings I have


~/.fetchmailrc

poll pop.gmail.com                   
with proto POP3                      
user 'exrs.2008@gmail.com'        
there with password '****'        
is 'exrs.2008' here                              
mda "/usr/bin/procmail -d %T"        
options                                                             
no keep                                 
ssl                                  
sslcertck                            
sslcertpath /etc/ssl/certs

*****************************************

echo $USER

qmemo

*****************************************

~/.procmailrc

PATH=/bin:/usr/bin:/usr/local/bin 
VERBOSE=off  
DEFAULT=/var/spool/mail/qmemo
MAILDIR=$HOME/mail            
LOGFILE=$HOME/.procmaillog

---

### Post by unutbu on 2009-05-21
In ~/.fetchmailrc, change
```

is 'exrs.2008' here 
```

to
```

is 'qmemo' here 
```

PS. andrew.46, you have written so many interesting and useful guides! Thank you, thank you, thank you!
This one helped me setup Gmail with emacs.

---

### Post by andrew.46 on 2009-05-21
Hi unutbu,

> **unutbu said:**
> In ~/.fetchmailrc, change
```

is 'exrs.2008' here 
```

to
```

is 'qmemo' here 
```

I think you have hit the nail on the head there :-).

> PS. andrew.46, you have written so many interesting and useful guides! Thank you, thank you, thank you!
This one helped me setup Gmail with emacs.

I am *very* pleased that you have profited from some of these guides! My dark secret is that in part I write them so I *myself* can learn the software better :-).

All the best,

Andrew

---

### Post by qmemo on 2009-05-22
Thank you for replying me, I changed the name as suggested and there is a new error :D

```

qmemo@some-where:~$ [COLOR=Red]*mutt*[/COLOR]
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Fri 22 May 2009 02:04:45 PM EEST: poll started
Trying to connect to 72.14.221.111/995...connected.
fetchmail: Issuer Organization: Equifax
fetchmail: Unknown Issuer CommonName
fetchmail: Server CommonName: pop.gmail.com
fetchmail: pop.gmail.com key fingerprint: 44:A8:E9:2C:FB:A9:7E:6D:F9:DB:F3:62:B2:9E:F1:A9
fetchmail: POP3< +OK Gpop ready for requests from 41.232.225.137 12pf1043654fgg.6
fetchmail: POP3> CAPA
fetchmail: POP3< +OK Capability list follows
fetchmail: POP3< USER
fetchmail: POP3< RESP-CODES
fetchmail: POP3< EXPIRE 0
fetchmail: POP3< LOGIN-DELAY 300
fetchmail: POP3< X-GOOGLE-VERHOEVEN
fetchmail: POP3< UIDL
fetchmail: POP3< .
fetchmail: POP3> USER exrs.2008@gmail.com
fetchmail: POP3< +OK send PASS
fetchmail: POP3> PASS *
fetchmail: POP3< +OK Welcome.
fetchmail: POP3> STAT
fetchmail: POP3< +OK 1 27520
fetchmail: POP3> LAST
fetchmail: POP3< -ERR Not supported
fetchmail: Not supported
fetchmail: POP3> UIDL
fetchmail: POP3< +OK
fetchmail: POP3< 1 GmailId12167fa93e5a364d
fetchmail: POP3< .
1 message for exrs.2008@gmail.com at pop.gmail.com (27520 octets).
fetchmail: POP3> LIST 1
fetchmail: POP3< +OK 1 27520
fetchmail: POP3> TOP 1 99999999
fetchmail: POP3< +OK message follows
reading message exrs.2008@gmail.com@gmail-pop.l.google.com:1 of 1 (27520 octets)
#**************************.*********************************.************************.**************.**************.**************.**********************************.******************************.*************************.***************.***************.*****************.***************.***********************************.**************************************************************.*************************************.***************************.**********************************.***************************.********************.*************************************.**************************.*********************************.**********************.********************.***************procmail: Renaming bogus mailbox "/var/mail/qmemo" info "/var/mail/BOGUS.qmemo.he-B"
 flushed
fetchmail: POP3> DELE 1
fetchmail: POP3< +OK marked for deletion
fetchmail: POP3> QUIT
fetchmail: POP3< +OK Farewell.
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Fri 22 May 2009 02:05:07 PM EEST: poll completed
fetchmail: normal termination, status 0
Press any key to continue...
You have new mail in /var/spool/mail/qmemo
qmemo@some-where:~$ [COLOR=Red]*mail*[/COLOR]
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/spool/mail/qmemo": 1 message 1 new

```I can only use 'mail' to view the Downloaded mail, but I can not with mutt!

here is .muttrc
```

#======================================================#
# Boring details
set realname = "qmemo"
set from = "exrs.2008@gmail.com"
set use_from = yes
set envelope_from ="yes"

# Use a signature
set signature="~/.signature"

# Use msmtp rather than sendmail. Check that 
# the path is correct for your system:
set sendmail="/usr/bin/msmtp"   

# If not set in ~/.bashrc:
set spoolfile = /var/spool/mail/qmemo

#======================================================#
# Folders
set folder="$HOME/mail"      # Local mailboxes stored here
set record="+sent"           # Where to store sent messages
set postponed="+postponed"   # Where to store draft messages
set mbox_type=mbox           # Mailbox type
set move=no                  # Don't move mail from spool

#======================================================#
# Watch these mailboxes for new mail, useful only if 
# Procmail or Maildrop is used to sort mail.
mailboxes ! +slrn +fetchmail +mutt
set sort_browser=alpha    # Sort mailboxes by alpha(bet)

#======================================================#
# What to show and order of headers
ignore *
unignore Date: From: User-Agent: X-Mailer X-Operating-System To: \
         Cc: Reply-To: Subject: Mail-Followup-To:
hdr_order Date: From: User-Agent: X-Mailer X-Operating-System To: \
        Cc: Reply-To: Subject: Mail-Followup-To:
                       
#======================================================#
# which editor do you want to use? 
# vim of course!
set editor="vim -c 'set tw=70 et' '+/^$' " 
set edit_headers=yes      # See the headers when editing

#======================================================#
# Aliases

set alias_file = ~/mail/mutt_aliases # In their own file
source ~/mail/mutt_aliases           # Source them
set sort_alias=alias                 # Sort alphabetically

#======================================================#
# Colours: defaults are a little bleak so experiment!

source ~/.mutt/mutt_colors            # In their own file 

#======================================================#
# Lists: An example using the mutt-users list:

lists mutt-users
subscribe mutt-users
set followup_to=yes        # Sets 'Mail-Followup-To' header
set honor_followup_to=yes  
fcc-hook mutt-user +mutt   # See your own posts using fcc

#======================================================#
# Odds and ends

set markers          # mark wrapped lines of text in the pager with a +
set smart_wrap       # Don't wrap mid-word
set pager_context=5  # Retain 5 lines of previous page when scrolling.
set status_on_top    # Status bar on top.
push <show-version>  # Shows mutt version at startup

macro index,pager I '<shell-escape> fetchmail -v<enter>'

```ok :popcorn:

---

### Post by qmemo on 2009-05-22
*//update//*

I re-wrote/checked the .muttrc & editied .procmailrc and it's working now as it should be :)

Thanks [andrew.46]("http://ubuntuforums.org/member.php?u=208550") and [unutbu]("http://ubuntuforums.org/member.php?u=518895")

---

### Post by andrew.46 on 2009-05-22
Hi qmemo,

> **qmemo said:**
> I re-wrote/checked the .muttrc & edited .procmailrc and it's working now as it should be :)

Glad to hear that it is all working now :-). I am on the wrong distro at the moment to check the exact location but search out the html docs one rainy day and you will see the almost limitless options to customise your .muttrc.

All the best,

Andrew

---

### Post by andrew.46 on 2009-05-24
Hi,

Took me a little while to return as I have been distro-hopping :-). For Jaunty the html docs for mutt can be found in /usr/share/doc/mutt/html. Docs are:

```

andrew@skamandros:/usr/share/doc/mutt/html$ ls
advancedusage.html   index.html   mimesupport.html       reference.html
configuration.html   intro.html   miscellany.html        tuning.html
gettingstarted.html  manual.html  optionalfeatures.html

```

and are highly recommended reading.

Andrew

---

### Post by Coffee Frapp on 2009-06-07
I've set up everything correctly, but when I fetchmail i get
```
chuck@chuck:~$ fetchmail
File /home/chuck/.fetchmailrc must be owned by you.

```so i run sudo fetchmail and
```
chuck@chuck:~$ sudo fetchmail
fetchmail: WARNING: Running as root is discouraged.
1 message for ubuntuscript@gmail.com at pop.gmail.com (1240 octets).
reading message ubuntuscript@gmail.com@gmail-pop.l.google.com:1 of 1 (1240 octets). not flushed

```Does anyone know what the problem could be? I've spent quite a bit of time on google with no luck.
What I'm trying to do is have the email contents display in the terminal.

edit: oh nevermind i think i misunderstood,

---

### Post by andrew.46 on 2009-06-08
Hi Coffee,

> **Coffee Frapp said:**
> 
```
chuck@chuck:~$ fetchmail
File /home/chuck/.fetchmailrc must be owned by you.

```

Sounds like you may have resolved the issue but just in case you have not I shall answer :-). Permissions and ownership of the fetchmail config file should be similar to the following:

```
andrew@skamandros~$ **[COLOR="Purple"]ls -l $HOME/.fetchmailrc[/COLOR]**
-rw------- 1 andrew users 458 2008-10-25 18:04 /home/andrew/.fetchmailrc
```

Can you post your own?

Andrew

---

### Post by Coffee Frapp on 2009-06-08
> **andrew.46 said:**
> Hi Coffee,



Sounds like you may have resolved the issue but just in case you have not I shall answer :-). Permissions and ownership of the fetchmail config file should be similar to the following:

```
andrew@skamandros~$ **[COLOR=Purple]ls -l $HOME/.fetchmailrc[/COLOR]**
-rw------- 1 andrew users 458 2008-10-25 18:04 /home/andrew/.fetchmailrc
```Can you post your own?

Andrew
Thanks, it turns out the permissions were for root, fixed it :)
```
-rw------- 1 root root 745 2009-06-07 21:06 /home/chuck/.fetchmailrc
```

---

### Post by andrew.46 on 2009-06-09
Hi Coffee Frapp,

> **Coffee Frapp said:**
> Thanks, it turns out the permissions were for root, fixed it :)
```
-rw------- 1 root root 745 2009-06-07 21:06 /home/chuck/.fetchmailrc
```

Good to hear, I hope you enjoy using mutt and gmail the old-fashioned way :-). If you were interested to see another way of collecting your mail from gmail with mutt just search google for 'mutt gmail IMAP'. I tried it for a while but could not warm to it at all :-).

All the best,

Andrew

---

### Post by Nyken on 2009-07-08
Heh, no one's posted here since 2006, but I always have to leave thanks to those who taught me something I really like using. I found this approach is more approachable in the email writing part, if the editor is changed to Nano in the .muttrc file. To do that, comment out that line with a ## and set the editor to = nano on a new line.

Very nice lightweight email app! Work for Rite Aid and we use Unix and this is alot like using the SYSM program for sending email. Very familiar.

---

### Post by andrew.46 on 2009-07-09
Hi Nyken,

> **Nyken said:**
> Heh, no one's posted here since 2006, but I always have to leave thanks to those who taught me something I really like using.

Thanks for taking the time to write this note :-). Mind you I suspect you may have misread the posting dates a little!

> I found this approach is more approachable in the email writing part, if the editor is changed to Nano in the .muttrc file. To do that, comment out that line with a ## and set the editor to = nano on a new line.


I have taken a little stick for suggesting vim, I sometimes forget that this editor which is so familiar to me from daily use poses an often insurmountable challenge to new users. I remember trying nano once and I found it quite difficult because of course the keystrokes are all different :-).

All the best,

Andrew

---

### Post by m0116815 on 2009-08-13
Hi,

Just wanted to thank Andrew for this tutorial. I'm a relative newbie to all things linux but have developed something of a fetish for console-only applications, so I love this easy low-threshold tutorial :)

Somewhat random but related question (I have no idea how to go about this): When I now press 'I' in mutt, it goes back to the terminal and shows me a lot of the fetchmail output that some people have posted above. I don't get errors, so all is well, but I'm usually not interested in the output fetchmail shows, and I'd like to get rid of the "press any key" system pause. Is there an easy way to tell fetchmail to go straight back to mutt after it's done its thing?

Thanks!

---

### Post by andrew.46 on 2009-08-13
Hi m0116815,

> **m0116815 said:**
> Just wanted to thank Andrew for this tutorial. I'm a relative newbie to all things linux but have developed something of a fetish for console-only applications, so I love this easy low-threshold tutorial :)

Thank you very much for your kind words!

> Somewhat random but related question (I have no idea how to go about this): When I now press 'I' in mutt, it goes back to the terminal and shows me a lot of the fetchmail output that some people have posted above. I don't get errors, so all is well, but I'm usually not interested in the output fetchmail shows, and I'd like to get rid of the "press any key" system pause. Is there an easy way to tell fetchmail to go straight back to mutt after it's done its thing?

Well I am not great at mutt macros but it looks like there is an easy answer for this one. Instead of the macro I give:

```

macro index,pager I '<shell-escape> fetchmail -v<enter>'

```

which I should mention was given to me by a kind member of the mutt-users mailing list try this variation which I have created and which works well on my system:

```

macro index,pager I '**[COLOR="Red"]<enter-command>unset wait_key<enter>[/COLOR]**<shell-escape>fetchmail -v<enter>'

```

Hopefully this will work on your system too?

Andrew

---

### Post by m0116815 on 2009-08-14
> **andrew.46 said:**
> try this variation which I have created and which works well on my system:

```

macro index,pager I '**[COLOR="Red"]<enter-command>unset wait_key<enter>[/COLOR]**<shell-escape>fetchmail -v<enter>'

```This works beautifully, thanks a lot! Using these commands as Google terms also helped me find my way to the relevant part of the mutt manual, which is going to be fun to play with.

Cheers!

---

### Post by andrew.46 on 2009-08-14
Hi m0116815,

> **m0116815 said:**
> This works beautifully, thanks a lot! Using these commands as Google terms also helped me find my way to the relevant part of the mutt manual, which is going to be fun to play with.

Excellent news :-). I should probably point out to other readers of this thread that the documentation for mutt is unusually comprehensive and on a Jaunty system the html manual and several other useful documents can be found in /usr/share/doc/mutt/html/ and many of these documents are well worth printing off and keeping by your side.

All the best,

Andrew

---

### Post by conehead77 on 2009-08-27
Thanks for this great tutorial!
I got so frustrated with mutt because nobody told me i would need something like fetchmail!

Finally i got a command line mail client up and running :)

---

### Post by andrew.46 on 2009-08-27
Hi conehead,

> **conehead77 said:**
> Thanks for this great tutorial!
I got so frustrated with mutt because nobody told me i would need something like fetchmail!

Finally i got a command line mail client up and running :)

Good to hear that you have it all running :-). Actually I illustrated this guide with *fetchmail* as I am a little set in my ways, many people are using *getmail* these days which is a little easier to get going.

All the best,

Andrew

---

### Post by andrew.46 on 2009-08-29
Hi aircondirect,

> **aircondirect said:**
> Mutt is not designed to suit everyone, including those without basic knowledge about the concept of mail, or those unwilling to perform configuration. mutt is even not designed for the mass of "average users", although it works well for them, too. For those who prefer a client to "just work somehow" rather than give dedicated best performance, other mail programs are probably better suited.

I see you have found the '[big-brother]("http://www.andrews-corner.org/mutt.html")' of this guide :-).

Andrew

---

### Post by Gatekeeper_NZ on 2009-08-29
Thanks for the Tutorial. I'm just getting into this whole terminal business, and even I got it working so that must say something about the author. Lots of fun. Even did the Vim tutorial, takes a little getting used to, but I'm sure if I use it enough I'll get the hang of it.

Thanks again,
Hayden

---

### Post by andrew.46 on 2009-08-29
Hi Hayden

> **Gatekeeper_NZ said:**
> Thanks for the Tutorial. I'm just getting into this whole terminal business, and even I got it working so that must say something about the author. Lots of fun. Even did the Vim tutorial, takes a little getting used to, but I'm sure if I use it enough I'll get the hang of it..

I an glad that you have found some use for this guide and I wish you all the best wih your continued exploration of mutt and the terminal :-).

Andrew

---

### Post by rdingram on 2009-08-29
If this is a stupid question please feel free to reprimand...

Would it be normal for me to setup a cron job for fetchmail to run every minute? Just to make sure my mailbox would be up to the minute current. And if I did have that cron job running would I be updated on the command line when there are new messages in my mailbox?

Thanks for any thoughts or lashings!

---

### Post by andrew.46 on 2009-08-29
Hi rdingram,

> **rdingram said:**
> Would it be normal for me to setup a cron job for fetchmail to run every minute?

There are several ways that mail can be checked with fetchmail and I will admit for the most part I always check my own mail manually. If you wanted a more automated setup cron would be an option but I suspect you might be better using the daemon that ships with fetchmail. If you want to experiment a little the daemon can be started from the commandline:

```
fetchmail -d 900
```

and this will run fetchmail every 900 seconds and process your existing $HOME/.fetchmailrc file each time. I would advise against every *minute* as this is a little unfriendly to the remote server.

Daemon mode can alternatively be set in your $HOME/.fetchmailrc as follows:

```
set daemon 900
```

and the daemon will run following your first fetchmail run. I am not sure about receiving notifications of new mail, although I suspect it can be done I have not really looked into this before.

> Thanks for any thoughts or lashings!

No lashings :-). Like you I am learning as I go, I welcome questions that encourage me to learn more and yours has been one of those questions...

Andrew

---

### Post by conehead77 on 2009-08-30
> **rdingram said:**
> If this is a stupid question please feel free to reprimand...

Would it be normal for me to setup a cron job for fetchmail to run every minute? Just to make sure my mailbox would be up to the minute current. And if I did have that cron job running would I be updated on the command line when there are new messages in my mailbox?

Thanks for any thoughts or lashings!

If you use IMAP you can just add the *idle* option to the .fetchmailrc. I just tested it and got promptly notified of a new mail.

---

### Post by anmys on 2009-10-12
Nice tutorial. 

I have a slightly different query (maybe OT to this thread). When I send mail via mutt+msmtp, I see the copy of the mail in sent-mail folder at gmail (checked via web interface). Is this normal? If so, can it be disabled as I already have a copy on my machine?

Regards.

---

### Post by andrew.46 on 2009-10-13
Hi anmys,

> **anmys said:**
>  When I send mail via mutt+msmtp, I see the copy of the mail in sent-mail folder at gmail (checked via web interface). Is this normal? If so, can it be disabled as I already have a copy on my machine

This is set at the gmail end and despite a decent look at the settings I could not see how to alter this. Sorry :(.

Andrew

---

### Post by Wobblybob on 2010-03-22
Thanks for this Andrew, I've finally sorted out my command line email need.

---

### Post by andrew.46 on 2010-03-24
Hi Wobblybob,

> **Wobblybob said:**
> Thanks for this Andrew, I've finally sorted out my command line email need.

It is my pleasure :).

Andrew

---

### Post by harry71194 on 2010-05-10
Hi! 

I am using mutt with a few alises (for mailing-lists and such).

> set reverse_name
set from = "mygmail@gmail.com"
alternates ".*@domain1.tld|.*@domain2.tld"
set use_from = yes
set envelope_from ="yes"
set use_envelope_from=yes

send-hook '~t ^hlds_linux@list\.valvesoftware\.com$' 'my_hdr From: Name <name.hlds@domain.tld>'


Only problem is, it *SHOULD* be sending out as my "From" field, but it isn't. My emails get bounced by the mailing-list saying I am not subscribed (as it sends to my gmail, not my custom domain alias)

What do I do? I don't want to sign up my gmail for mailinglists, I want to use my other aliases.. :|
I can't raw send the mail, as my ISP is in spamhaus ( [http://www.spamhaus.org/pbl/query/PBL283756](http://www.spamhaus.org/pbl/query/PBL283756) )

Help please!

---

### Post by andrew.46 on 2010-05-11
Hi harry71194,

If you wish to use gmail to send these extra addresses in the 'From:' field you will have to take an extra step at the Gmail end (web interface) under:

Settings ---> Accounts and Import ---> Send mail as:

and add the addresses in + walk though the confirmation process that Gmail requires. Hope that helps?

Andrew

---

### Post by harry71194 on 2010-05-11
> **andrew.46 said:**
> Hi harry71194,

If you wish to use gmail to send these extra addresses in the 'From:' field you will have to take an extra step at the Gmail end (web interface) under:

Settings ---> Accounts and Import ---> Send mail as:

and add the addresses in + walk though the confirmation process that Gmail requires. Hope that helps?

Andrew
Hiya, I think I already did that before. The email address is right there on the list in my "Send mail as" section. :/

Might I need to make a new user-account per email address? My domain's email is handled by Gmail Apps.

Example: [email]harry@mydomain.tld[/email] is under [email]mygmail@gmail.com[/email]'s "From" options in the web interface. Anything else I need to see?

---

### Post by andrew.46 on 2010-05-11
Hi harry,

I am afraid I am not completely sure of the solution then. The definitive guide for the Google end is here:

[http://mail.google.com/support/bin/answer.py?answer=22370](http://mail.google.com/support/bin/answer.py?answer=22370)

but it sounds as if you have this set already...

Sorry,

Andrew

---

### Post by soorjithp on 2010-05-19
Hi

thanks for this article.
after done the installation, I have simply tried the mutt command in a terminal 

eg:- mutt -s "Test mail" [email]soorjithp@gmail.com[/email] <a.txt

it works, I got the contents in a.txt as a new mail in my mailbox.

but when I tried to put an attachment it fails.

Pls let me know can we do an attachment with this.

Regards
Soorjith P

---

### Post by brijith on 2010-05-20
> **soorjithp said:**
> Hi
but when I tried to put an attachment it fails.
Pls let me know can we do an attachment with this.


Hi how you tried to attach file. Can you give the command you tried?

one example is given below
mutt -s "subject" -a "file to attach" "e-mail address"< mail body.txt"

---

### Post by soorjithp on 2010-05-20
ys exactly same

---

### Post by brijith on 2010-05-20
Hi,

Are you getting any error.. 
Can you paste the out put of that command

---

### Post by soorjithp on 2010-05-20
no error

---

### Post by brijith on 2010-05-20
> **soorjithp said:**
> no error

are you sure that the path you given to the file to attach is correct. Please check it

---

### Post by soorjithp on 2010-05-20
sure

---

### Post by Ankersman on 2010-07-04
Big thanks to Andrew.46

---

### Post by andrew.46 on 2010-07-05
Hi Ankersman,

> **Ankersman said:**
> Big thanks to Andrew.46

My pleasure :).

Andrew

---

### Post by adibas on 2010-07-05
Thank you
;)

> **andrew.46 said:**
> Hi pajoohesh,

Thanks again for your feedback:



I experimented with these methods and unfortunately could not get them to work as you have mentioned using mutt.



Perfectly understandable. Bear in mind that the setting of 0600 actually means that only yourself and root can read and alter this file, so the password is not *completely* exposed. However I have noticed that Version 1.4.17 of msmtp was released only recently and this version has support for the Gnome keyring. Details can be seen in [the changelog]("http://msmtp.cvs.sourceforge.net/*checkout*/msmtp/msmtp/ChangeLog").

I had a quick look at the source for 1.4.17 and saw the new option:

```
./configure --with-gnome-keyring 
```which is exactly what you are after :-). However this is a very new version, only 2 or 3 days old, and not available even in the upcoming Jaunty Jackalope yet and it is beyond the scope of this guide to demonstrate how to compile this one.

You may very well be better off to wait for a decent debiam package of the new msmtp to be released and then hide your password in the keychain. Sorry for not having a better answer :(.

All the best,

Andrew

---

### Post by Bertus_Nel on 2010-07-06
First and foremost - thanks for the great "How to" - however I have a problem. I did everything you said and mutt is configured in junction with your config (My account details though) :-)  - when I run Fetchmail -v I get the following:

"fetchmail -v
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Tue 06 Jul 2010 14:49:26 SAST: poll started
Trying to connect to 74.125.39.109/995...connection failed.
fetchmail: connection to pop.gmail.com:pop3s [74.125.39.109/995] failed: Connection timed out.
POP3 connection to pop.gmail.com failed: Connection timed out
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Tue 06 Jul 2010 14:52:35 SAST: poll completed
fetchmail: Query status=2 (SOCKET)
fetchmail: normal termination, status 2
"

Going through Mozilla works fine and can login to my Gmail - but fetchmail seems to have a glitch.

Second issue:

Now if I run mutt from terminal I get the following:

Error in /home/bertus/.muttrc, line 2: ring: unknown command
source: errors in /home/bertus/.muttrc

Here is the first few lines of my muttrc config file: 

ring details
set realname = "Bertus Nel"
set from = "pabnel.nel@gmail.com"
set use_from = yes
set envelope_from ="yes"
set sendmail="/usr/bin/msmtp"

And when I enter mutt and ignore the errors, this is what I get when i want to send a mail out of mutt:

msmtp: /home/bertus/.msmtprc: must have no more than user read/write permissions - I have set the rights via GUI to read/write only but still no luck.


Ive been searching all over and cant seem to find a sollution to my agony. This is my last resort to ask one of you guys as Im also still new in this - going for 8 months on Linux. IF someone has a moment and can point me in the correct direction I will appreciate it.

---

### Post by andrew.46 on 2010-07-07
Hi Bertus,

> **Bertus_Nel said:**
> First and foremost - thanks for the great "How to" 

My pleasure :). I have to admit that I do not run Ubuntu at the moment but I try to still give a measure of support to the guides I have scattered across these forums. 

> - however I have a problem. I did everything you said and mutt is configured in junction with your config (My account details though) :-)  - when I run Fetchmail -v I get the following:

"fetchmail -v
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Tue 06 Jul 2010 14:49:26 SAST: poll started
Trying to connect to 74.125.39.109/995...connection failed.
fetchmail: connection to pop.gmail.com:pop3s [74.125.39.109/995] failed: Connection timed out.
POP3 connection to pop.gmail.com failed: Connection timed out
fetchmail: 6.3.9-rc2 querying pop.gmail.com (protocol POP3) at Tue 06 Jul 2010 14:52:35 SAST: poll completed
fetchmail: Query status=2 (SOCKET)
fetchmail: normal termination, status 2
"

Going through Mozilla works fine and can login to my Gmail - but fetchmail seems to have a glitch.

You will find that the POP3 connection can be a little flaky some days, as it has been for several days from my part of the world. If the POP3 connection details are definitely setup [at the gmail end]("http://mail.google.com/support/bin/answer.py?hl=en&answer=13273") I would suspect that you simply need to wait until the Gmail end is fixed.

> Second issue:

Now if I run mutt from terminal I get the following:

Error in /home/bertus/.muttrc, line 2: ring: unknown command
source: errors in /home/bertus/.muttrc

Here is the first few lines of my muttrc config file: 

```
ring details
set realname = "Bertus Nel"
set from = "pabnel.nel@gmail.com"
set use_from = yes
set envelope_from ="yes"
set sendmail="/usr/bin/msmtp"
```



I am afraid you have made a glorious copy and paste error :). The first line should actually be commented out:

```
**[COLOR="Red"]# Bo[/COLOR]**ring details
```


> And when I enter mutt and ignore the errors, this is what I get when i want to send a mail out of mutt:

msmtp: /home/bertus/.msmtprc: must have no more than user read/write permissions - I have set the rights via GUI to read/write only but still no luck.

The easiest way is to set it from the commandline:

```
chmod 0600 $HOME/.msmtprc
```

If this still does not work could you post the results of:

```
ls -l $HOME/.msmtprc

```

and the solution will not be difficult I suspect.

All the best,

Andrew

---

### Post by jaredssix on 2010-07-07
Hey all. I am a mutt user. My system runs IMAP and SMTP through gmail. 

My only complaint is there is lag time in reading and sending emails. OfflineIMAP  seems to expedite the reading part of the conundrum. Would msmtp expedite the sending part of the conundrum?

I guess my goal is to be able to quickly read an email, and to tap "y" for send and move on to the next email without having to wait for the email to send . . .

Suggestions?

---

### Post by andrew.46 on 2010-07-17
Hi jaredssix,

Unfortunately my experience has always been using gmail with pop3 rather than imap :(. I remember dabbling briefly with imap but I prefer the old-fashioned way...

Andrew

---

### Post by jaredssix on 2010-07-17
Thanks for responding, Andrew--I see from your posts you've been a great service to mutt users!

I did realize my issue, and it was as simple as a typo in my muttrc--always the most difficult errors to find!

So, I do have mutt set up, IMAP, with msmtp and offlineimap (triggered through cron)--and it is lightning fast! All my emails are backed up and synced on my hard drive, and my email account. The msmtp setting "set sendmail_wait = -1" is critical to the speed of this interface.

If anyone has questions regarding this set up, feel free to reply to this post . . .

---

### Post by Bertus_Nel on 2010-07-22
Thanks a Million Andrew - I will have look and fix my stupid mistake. :D Im running a few projects at work and will within the next week post the results. 

You all have a awesome day.

---

### Post by Bertus_Nel on 2010-07-23
Hi Andrew

Ok, I did what you said I must do - when I compose and email and want to send it I get the following: "msmtp: /home/bertus/.msmtprc: must be owned by you" I did assign the rights as requested. This is the last hurdle I assume.

Thanks for your help, you a legend.;)

---

### Post by andrew.46 on 2010-07-23
Hi Bertus,

> **Bertus_Nel said:**
> Ok, I did what you said I must do - when I compose and email and want to send it I get the following: "msmtp: /home/bertus/.msmtprc: must be owned by you" I did assign the rights as requested.

Almost there :) Easiest way to see who actually owns the file is to run:

```
ls -l $HOME/.msmtprc
```

and then it will be a simple matter to change the ownership of the file...

All the best,

Andrew

---

### Post by TruViet911 on 2010-09-15
thanks but how do you send mail? i type m to compose email and everything but where is the send button or command key for sending email? help

---

### Post by andrew.46 on 2010-09-15
Hi TrueViet,

> **TruViet911 said:**
> thanks but how do you send mail? i type m to compose email and everything but where is the send button or command key for sending email? help

The key by default is 'y', you should see it at the bottom left of the screen on the Compose window marked 'y:Send'.

Andrew

---

### Post by TruViet911 on 2010-09-15
> **andrew.46 said:**
> Hi TrueViet,



The key by default is 'y', you should see it at the bottom left of the screen on the Compose window marked 'y:Send'.

Andrew

Hi Andrew, 
thanks for response but unfortunately i don't see that option. when i press m to compose a new message. it ask me for To: and Subject. that's all there are no menu or anything. i was reading mutt manual and the default key for send mail is y just like u said. but when i press y it didn't do anything. 

what did i do wrong?

---

### Post by andrew.46 on 2010-09-16
Hi TruViet,

> **TruViet911 said:**
> thanks for response but unfortunately i don't see that option. when i press m to compose a new message. it ask me for To: and Subject. that's all there are no menu or anything. i was reading mutt manual and the default key for send mail is y just like u said. but when i press y it didn't do anything. 

I think I see the problem. Are you using vim to create your email? If so you need to create your message and then save it (usually with :wq! ), you will then go to the screen from which you can send your message. I attach a screenshot to illustrate this final screen.

Andrew

---

### Post by TruViet911 on 2010-09-16
> **andrew.46 said:**
> Hi TruViet,



I think I see the problem. Are you using vim to create your email? If so you need to create your message and then save it (usually with :wq! ), you will then go to the screen from which you can send your message. I attach a screenshot to illustrate this final screen.

Andrew

Yea i use Vim for all my editing. anyways Thanks alot Andrew. it works like a charm now i need to play around with the colors. i wonder if i can integrate vim plug-ins within mutt :D):P

---

### Post by andrew.46 on 2010-09-16
Hi TruViet,

> **TruViet911 said:**
> [...] it works like a charm now i need to play around with the colors.P

Good to hear it is all working now! As for the colours it might be worth a quick look at this guide's big brother:

Using Mutt with Gmail
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

where there is a small section on manipulating colours, but only a starting guide really.

All the best,

Andrew

---

### Post by c2tarun on 2010-09-23
hi andrew
i am dropping my thread now and i'll ask all my problems here only.
can you please explain what is the function of the two lines starting with tls.
and what will the log file store.???
thanx

---

### Post by andrew.46 on 2010-09-23
Hi ctarun,

> **c2tarun said:**
> 
can you please explain what is the function of the two lines starting with tls.
and what will the log file store.???

TLS stands for 'Transport Layer Security' and is used in in this case to provide security for your outgoing mail, the first tls command starts this protocol. The second tls command points to the certificate that is used to authenticate the remote server, this is obtained from the certificate pack held in the Ubuntu repository,

A typical example of the msmtp log is as follows, drawn from my own logfile (I have altered the email addresses):

```

Sep 21 19:14:03 host=smtp.gmail.com tls=on auth=on user=andrew.46 from=andrew.46@gmail.com recipients=andrew@slackware.com mailsize=1159 smtpstatus=250 smtpmsg='250 2.0.0 OK 1285060436 h8sm8933317ibk.15' exitcode=EX_OK

```

This log will show why messages have failed and is especially useful when gmail change their certificates :).

Andrew

---

### Post by PoPpiLLs on 2010-09-25
hanks andrew.46 I just set up mutt and I'm loving it, its so much you can do I don't know where to start.

---

### Post by andrew.46 on 2010-09-25
Hi PoPpiLLs,

> **PoPpiLLs said:**
> Thanks andrew.46 I just set up mutt and I'm loving it, its so much you can do I don't know where to start.

My pleasure :). There is a very comprehensive manual in html that will provide an excellent start, indeed there are many, many, many options :).

Andrew

---

### Post by roy.zyo on 2011-01-22
Andrew.46! Thank you =D


human@pc-1:~$ ls -l $HOME/.procmailrc
-rw-r--r-- 1 root root 287 2011-01-22 20:19 /home/human/.procmailrc
human@pc-1:~$ chmod 0644 $HOME/.procmailrc
chmod: changing permissions of `/home/human/.procmailrc': Operation not permitted
human@pc-1:~$ sudo chmod 0644 $HOME/.procmailrc
[sudo] password for human: 
human@pc-1:~$ ls -l $HOME/.procmailrc
-rw-r--r-- 1 **root root** 287 2011-01-22 20:19 /home/human/.procmailrc
human@pc-1:~$ sudo chmod 600 $HOME/.procmailrc
human@pc-1:~$ ls -l $HOME/.procmailrc
-rw------- 1 **root root** 287 2011-01-22 20:19 /home/human/.procmailrc
human@pc-1:~$ sudo chmod 0644 $HOME/.procmailrc

umm, how to change the permission to "human"? 

I still can get it working by

macro index,pager I '<shell-escape> **sudo** fetchmail -v<enter>'

---

### Post by andrew.46 on 2011-01-27
Hi roy,

> **roy.zyo said:**
> 

```
human@pc-1:~$ ls -l $HOME/.procmailrc
-rw------- 1 **root root** 287 2011-01-22 20:19 /home/human/.procmailrc
human@pc-1:~$ sudo chmod 0644 $HOME/.procmailrc
```

umm, how to change the permission to "human"? 


You are after chown:

```
sudo chown human:human /home/human/.procmailrc
```

I don't have Ubuntu installed at the moment, I have a dim memory that it should be *human:human* on Ubuntu, I am more used to using *human:users* on my current system. Have a quick look at the ownership of other files in $HOME to be sure.

Andrew

---

### Post by Turgon_Noldor on 2011-03-13
Well, i guess i am on the list of new mutt users :D
Of all the tutorials i have read this far, this is by far the most straighforward! Thank you so much Andrew!!

Though i have a couple of questions:

[LIST=1]
[*]is there a way to get the mail sorted following the labels i have set on the GUI interface?
[*]And how can i read the mail i have saved from the mutt interface??
[*]Could you please re-explain how to configure security for the msmtp password using the keyring??
[/LIST]
Thank you again, :)

---

### Post by Turgon_Noldor on 2011-03-13
Btw, Andrew, shouldn't you add that in the .muttrc the value of sendmail should be msmtp?
I struggled with this for a while before finding out your online tutorial [here]("http://www.andrews-corner.org/mutt.html") which is quite more complete than this one!

Anyway, thank you so much again and again :D

---

### Post by TheDexter1111 on 2011-03-15
brilliant tutorial mate! worked a treat :) I honestly cant believe it worked first time (for me anyway) lol

---

### Post by K_REY_C on 2011-03-17
I'm using Mutt with Gmail -- just got it set up -- but I'm having a problem.

The newest mail that I see in my mailbox is from July of 2009. POP on gmail is set up to allow download of all of the mail. 

Any thoughts?

Thanks!

---

### Post by andrew.46 on 2011-03-17
> **Turgon_Noldor said:**
> Btw, Andrew, shouldn't you add that in the .muttrc the value of sendmail should be msmtp?
I struggled with this for a while before finding out your online tutorial [here]("http://www.andrews-corner.org/mutt.html") which is quite more complete than this one!

Well actually that website is aimed more at a general Linux audience of course, but I believe the sendmail line is present in the Ubuntu version as well?

Andrew

---

### Post by andrew.46 on 2011-03-17
> **TheDexter1111 said:**
> brilliant tutorial mate! worked a treat :) I honestly cant believe it worked first time (for me anyway) lol

I am glad that the guide has worked well for you :). I forget sometimes that there are so many people who get though this guide with no issues at all!

---

### Post by andrew.46 on 2011-03-17
> **K_REY_C said:**
> The newest mail that I see in my mailbox is from July of 2009. POP on gmail is set up to allow download of all of the mail.

I suspect you have run into a Gmail limitation which decides how many messages can be downloaded at a time. Either keep downloading or change the dates for POP3 access should do the trick.

Andrew

---

### Post by andrew.46 on 2011-03-17
> **Turgon_Noldor said:**
> Well, i guess i am on the list of new mutt users :D
Of all the tutorials i have read this far, this is by far the most straighforward! Thank you so much Andrew!!

Glad it has worked for you :). I admit with some shame that I have not really looked at this guide for a while so it is good news that it still works!!

> 
[LIST=1]
[*]is there a way to get the mail sorted following the labels i have set on the GUI interface?
[*]And how can i read the mail i have saved from the mutt interface??
[*]Could you please re-explain how to configure security for the msmtp password using the keyring??
[/LIST]


1. As far as I know this is not possible although I have vague memories of hearing that something like this is possible with IMAP, which I have only dabbled with briefly before deciding that I cordially disliked it :).
2. You should be able to open the mail with any standard text editor such as gedit, vim etc.
3. I have not used msmtp with gnome keyring I am afraid...

Andrew

---

### Post by gabala on 2011-10-13
Thanks a lot worked for me.

Actually last night when I installed Mutt I was not sure if my installation was right. and I had no idea how to send email with it. but tonight when I was browsing and saw this command and I tested it I found my my configuration is working and was correct from last night.

It is good to add this to your post is will be very useful to send email from command line.:

```
echo "Hello my friend!"|mutt -s "Greetings" friend.of.jhon@gmail.com
```

---

### Post by andrew.46 on 2011-10-13
Good to hear this guide has been useful to you :). I had actually suspected that this guide was slowly fading away...

---

### Post by andrew.46 on 2012-01-12
I have found a partition for Oneiric Ocelot and made the few small changes needed to bring this guide up to speed with the latest Ubuntu release. I hope that this will tempt a few more bold users to enter the world of mutt!

---

### Post by andrew.46 on 2012-04-13
This guide has been converted to a wiki:

[https://help.ubuntu.com/community/MuttAndGmail](https://help.ubuntu.com/community/MuttAndGmail)

but help is still available via this Forum thread :)

---

