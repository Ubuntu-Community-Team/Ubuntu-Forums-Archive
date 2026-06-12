---
title: "Pidgin 2.5 Released"
date: 2008-08-19
forum: The Cafe
---

### Post by 34.50 on 2008-08-19
[http://www.pidgin.im]("http://www.pidgin.im")

Version 2.5 out now. 

How do I install it since it's not in the repos yet?

---

### Post by Depressed Man on 2008-08-19
You can either compile it. Or wait for a getdeb version of it. Or if you know someone who has a repo with the latest version (I forget who has one..)

---

### Post by 34.50 on 2008-08-19
yeah when i try to compile something, something breaks along the process lol.

---

### Post by Nepherte on 2008-08-19
Try:
```
sudo apt-get install build-essential && sudo apt-get build-dep pidgin
```

---

### Post by Kosimo on 2008-08-19
Hello guys, pidgin folks has just released a new version 2.5.0

Here the changelog: 

Version 2.5.0

> 

    * libpurple
          o Ability to create custom smileys (currently only the MSN protocol utilizes the feature). (Thanks to Mauro Sérgio Ferreira Brasil, Marcus Lundblad, Jorge Villaseñor and other contributors)
          o Add a configure option, --with-system-ssl-certs to allow packagers to specify a system-wide SSL CA certificates directory. When set, we don't install our SSL CA certs, so it's important that the libpurple package depend on the CA certificates.
          o Add SSL Certificates support to the NSS SSL plugin. (Thanks to Lou Cipher) 

    * XMPP
          o Fix a bug that caused the UI to not refresh and caused the client to use 99% CPU when an XMPP account lost its connection to the server.
          o Possibly fix a bug where some clients could get into a state where they moved a buddy back and forth between two groups in an endless loop. 

    * IRC
          o /ctcp command (Vladislav Guberini&#263;)
          o Allow for auto-detection of incoming UTF-8 formatted text on accounts which are configured to use some other encoding. 

    * MSN
          o Update MSN support to protocol 15 (Elliott Sales de Andrade, Jorge Villaseñor, Mike Ruprecht, Carlos Silva, Ma Yuan, Daniel Ljungborg and others)
          o Personal messages are now supported. They are treated as status messages.
          o Offline IM is now supported.
          o Aliasing is now supported server-side.
          o Buddies are now emblemed. Bots and web clients should now be distinguished.
          o Update smiley set for non-faces.
          o Failing to update a buddy icon when the buddy has gone offline no longer crashes.
          o Custom smileys received in a chat no longer go to a new window.
          o Processing is no longer completely frozen after the servers block a message because it contains (what they consider) inappropriate text. 

    * Pidgin
          o Custom buddy icons can now be added to and removed from buddy list entries via the buddy list entry right-click menu.
          o Resize large incoming custom smileys to a maximum of 96px on either side.
          o Offer to add new buddies into the same contact as existing buddies in the same group if the alias given is the same.
          o Minor smiley style update. 

    * General
          o Group and Chat buddy list entries can now be given custom buddy icons. 

    * Finch
          o Added "Invite..." menu to chats.
          o Added "View All Logs" menu in the buddylist to display a list of all IM logs.
          o Added '/msgcolor' command to change colors of different classes of messages in a conversation. See '/help msgcolor' for details.
          o Added tab-completion for commands in conversation windows. 

    * Windows-specific changes
          o Don't install the GSSAPI SASL plugin on NT4 to avoid an error popup.
          o Use the Kerberos for Windows libraries installed on the system (if present) instead of including enough to load the plugin (Kfw still needed to be installed for it to actually work before this change).
          o Upgrade to Perl 5.10 (System Perl runtime must be upgraded for Perl plugins to continue to work).
          o Upgrade SILC to use the 1.1.7 toolkit 



As always:
Download the source, 
then:  
```
./configure
make
sudo aptitude install
```

---

### Post by SlugO on 2008-08-19
Now **this** is the update that I've been waiting for a looong time. MSN support is finally brought up to date from the prehistoric ages with MSNP15! :) :guitar:
Changelog:
>     * libpurple
          o Ability to create custom smileys (currently only the MSN protocol utilizes the feature). (Thanks to Mauro Sérgio Ferreira Brasil, Marcus Lundblad, Jorge Villaseñor and other contributors)
          o Add a configure option, --with-system-ssl-certs to allow packagers to specify a system-wide SSL CA certificates directory. When set, we don't install our SSL CA certs, so it's important that the libpurple package depend on the CA certificates.
          o Add SSL Certificates support to the NSS SSL plugin. (Thanks to Lou Cipher) 

    * XMPP
          o Fix a bug that caused the UI to not refresh and caused the client to use 99% CPU when an XMPP account lost its connection to the server.
          o Possibly fix a bug where some clients could get into a state where they moved a buddy back and forth between two groups in an endless loop. 

    * IRC
          o /ctcp command (Vladislav Guberini&#263;)
          o Allow for auto-detection of incoming UTF-8 formatted text on accounts which are configured to use some other encoding. 

    * MSN
          o Update MSN support to protocol 15 (Elliott Sales de Andrade, Jorge Villaseñor, Mike Ruprecht, Carlos Silva, Ma Yuan, Daniel Ljungborg and others)
          o Personal messages are now supported. They are treated as status messages.
          o Offline IM is now supported.
          o Aliasing is now supported server-side.
          o Buddies are now emblemed. Bots and web clients should now be distinguished.
          o Update smiley set for non-faces.
          o Failing to update a buddy icon when the buddy has gone offline no longer crashes.
          o Custom smileys received in a chat no longer go to a new window.
          o Processing is no longer completely frozen after the servers block a message because it contains (what they consider) inappropriate text. 

    * Pidgin
          o Custom buddy icons can now be added to and removed from buddy list entries via the buddy list entry right-click menu.
          o Resize large incoming custom smileys to a maximum of 96px on either side.
          o Offer to add new buddies into the same contact as existing buddies in the same group if the alias given is the same.
          o Minor smiley style update. 

    * General
          o Group and Chat buddy list entries can now be given custom buddy icons. 

    * Finch
          o Added "Invite..." menu to chats.
          o Added "View All Logs" menu in the buddylist to display a list of all IM logs.
          o Added '/msgcolor' command to change colors of different classes of messages in a conversation. See '/help msgcolor' for details.
          o Added tab-completion for commands in conversation windows. 

    * Windows-specific changes
          o Don't install the GSSAPI SASL plugin on NT4 to avoid an error popup.
          o Use the Kerberos for Windows libraries installed on the system (if present) instead of including enough to load the plugin (Kfw still needed to be installed for it to actually work before this change).
          o Upgrade to Perl 5.10 (System Perl runtime must be upgraded for Perl plugins to continue to work).
          o Upgrade SILC to use the 1.1.7 toolkit 

---

### Post by phrostbyte on 2008-08-19
Great release for MSN users.

---

### Post by aaaantoine on 2008-08-19
After configure...

```
Build with GStreamer support.. : yes
Build with D-Bus support...... : yes

. . .

Install pixmaps............... : yes
Install translations.......... : yes
Has you....................... : yes
```

Nooo! Pidgin 2.5.0 has me!

By the way, "apt-get build-dep pidgin" missed networkmanager-dev.  So be sure to install that too, or run ./configure with the option "--disable-nm" (not that I understand the importance of using nm, but I wouldn't recommend disabling it).

EDIT: Done configuring, making, and installing.  Now I get this error:

```
pidgin: symbol lookup error: pidgin: undefined symbol: purple_smileys_get_all
```

The solution to this? Make sure you run the following before you install:
```
$ sudo apt-get remove pidgin libpurple0
```
I had already removed pidgin, but not libpurple0.  That apparently spawned the error.

---

### Post by aaaantoine on 2008-08-19
"sudo aptitude install"?  Haven't tried that one before...

Mods, please merge with this thread: [http://ubuntuforums.org/showthread.php?t=894473](http://ubuntuforums.org/showthread.php?t=894473)

---

### Post by mrgnash on 2008-08-19
Almost makes me wish I used MSN.... no, wait, it doesn't :P

I'll install it anyway though.

Your instructions should also include the step of removing any existing installation of Pidgin before installing the latest version. I'm also not aware that 'sudo aptitude install' works for installing from source? But maybe I just haven't been clued in on that one ;)

---

### Post by RATM_Owns on 2008-08-19
GetDeb.net has .debs for it: [http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

---

### Post by picpak on 2008-08-19
> **aaaantoine said:**
> "sudo aptitude install"?  Haven't tried that one before...

That would be a typo. I assume he means "sudo checkinstall".

---

### Post by Tom--d on 2008-08-19
YAY!

I've been waiting for this for ages! :D
Finally Msn with personal Messages .. 

but, how do I have my own?

---

### Post by bruce89 on 2008-08-19
If only telepathy-butterfly could do all the libpurple stuff. Perhaps I should go back to telepathy-haze for MSN.

---

### Post by picpak on 2008-08-19
> **Tom--d said:**
> Finally Msn with personal Messages .. 

FINALLY!

Up next: plugin to set your personal message to the music you're playing. Then I might switch back...

---

### Post by Tom--d on 2008-08-19
> **picpak said:**
> FINALLY!

Up next: plugin to set your personal message to the music you're playing. Then I might switch back...

Yeah :D
And then.. I would recommend it to my friends (who are on Windows) than windows live messenger.

Talking of WLM. I was on windows today. Good computer. 1GB Ram. XP etc.
but, wlm was so slow. It takes ages to load.. then logging in has a freezing part. Just really (to me) a heavy application (or looks it to me).

---

### Post by Sef on 2008-08-19
Merged.

---

### Post by drubin on 2008-08-19
Just upgraded, works pretty well for now. The fact that it has msn offline messaging is amazing. (but I got a lot because I have never really be able to check them).

---

### Post by drubin on 2008-08-19
> **Tom--d said:**
> Yeah :D
And then.. I would recommend it to my friends (who are on Windows) than windows live messenger.

I already use Pidgin on windows at work.

---

### Post by Polygon on 2008-08-19
> **Tom--d said:**
> YAY!

I've been waiting for this for ages! :D
Finally Msn with personal Messages .. 

but, how do I have my own?

its whatever your status message is on pidgin

you can set your self as available then type a message in the little box, and then that will show up as your personal message.

---

### Post by bjschuma on 2008-08-19
> **picpak said:**
> FINALLY!

Up next: plugin to set your personal message to the music you're playing. Then I might switch back...

There's a script in Amarok that does this.  It's called "AmarokPidgin."

---

### Post by picpak on 2008-08-19
> **bjschuma said:**
> There's a script in Amarok that does this.  It's called "AmarokPidgin."

Would that script still try to run when Pidgin isn't, though? I know my AWN script tries to.

---

### Post by Toupee on 2008-08-19
Hooray for custom buddy icons! Finally!

---

### Post by midtown on 2008-08-20
> **mrgnash said:**
> I'm also not aware that 'sudo aptitude install' works for installing from source? But maybe I just haven't been clued in on that one ;)

I assume that is meant to be 'sudo make install'.

---

### Post by aaaantoine on 2008-08-20
Is anyone else getting frequent crashes?

---

### Post by drubin on 2008-08-20
> **aaaantoine said:**
> Is anyone else getting frequent crashes?

My one hasn't crashed once, Have you tried disabling all your plugins and  then re enabling them one at a time (after some time) to see which one causes more crashes.

---

### Post by Superkoop on 2008-08-20
Good to see Pidgin getting a bit better! :biggrin:
Now all I need is Webcam + audio and then I will switch. ;)

---

### Post by aaaantoine on 2008-08-20
> **rubinboy said:**
> My one hasn't crashed once, Have you tried disabling all your plugins and  then re enabling them one at a time (after some time) to see which one causes more crashes.

My current theory is that it crashes when I receive a message while a Flash animation is going (Flash being rendered by Adobe Flash 9 via nspluginwrapper :-|).

I'll try disabling plug-ins if it happens outside those circumstances.

---

### Post by DougieFresh4U on 2008-08-20
I thought I would try the new pigdin, but i am getting dependency from hell drama. I am trying to use the getdeb.  Can some one maybe assist me a little. Also I can never install a tar file unles I am supplied with exact code step by step
Thanks

---

### Post by picpak on 2008-08-20
> **DougieFresh4U said:**
> I thought I would try the new pigdin, but i am getting dependency from hell drama. I am trying to use the getdeb.  Can some one maybe assist me a little. Also I can never install a tar file unles I am supplied with exact code step by step
Thanks

Go to [http://getdeb.net/release.php?id=3099](http://getdeb.net/release.php?id=3099) and download **all** the files: pidgin, pidgin-data and libpurple0. Then open up a terminal and run:

```
sudo dpkg -i libpurple0_2.5.0-1~getdeb1_i386.deb pidgin-data_2.5.0-1~getdeb1_all.deb pidgin_2.5.0-1~getdeb1_i386.deb
```

Hope this helps. :)

---

### Post by LookTJ on 2008-08-20
> **DougieFresh4U said:**
> I thought I would try the new pigdin, but i am getting dependency from hell drama. I am trying to use the getdeb.  Can some one maybe assist me a little. Also I can never install a tar file unles I am supplied with exact code step by step
ThanksAre you getting the pidgin deb package from getdeb? If so, you have to install the required packages before installing the main package.

---

### Post by DougieFresh4U on 2008-08-20
> **picpak said:**
> Go to [http://getdeb.net/release.php?id=3099](http://getdeb.net/release.php?id=3099) and download **all** the files: pidgin, pidgin-data and libpurple0. Then open up a terminal and run:

```
sudo dpkg -i libpurple0_2.5.0-1~getdeb1_i386.deb pidgin-data_2.5.0-1~getdeb1_all.deb pidgin_2.5.0-1~getdeb1_i386.deb
```

Hope this helps. :)
Thanks for reply
this is what happened:
dougie@DougiesLeanMachine:~$ sudo dpkg -i libpurple0_2.5.0-1~getdeb1_i386.deb pidgin-data_2.5.0-1~getdeb1_all.deb pidgin_2.5.0-1~getdeb1_i386.deb
[sudo] password for dougie: 
dpkg: error processing libpurple0_2.5.0-1~getdeb1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing pidgin-data_2.5.0-1~getdeb1_all.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing pidgin_2.5.0-1~getdeb1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libpurple0_2.5.0-1~getdeb1_i386.deb
 pidgin-data_2.5.0-1~getdeb1_all.deb
 pidgin_2.5.0-1~getdeb1_i386.deb
dougie@DougiesLeanMachine:~$

---

### Post by virx on 2008-08-20
Is it going to be in repos? When? Who knows?

---

### Post by DougieFresh4U on 2008-08-20
> **Taylor said:**
> Are you getting the pidgin deb package from getdeb? If so, you have to install the required packages before installing the main package.

Tried to install all three but each one had a different dependency poblem

---

### Post by ghindo on 2008-08-20
> **virx said:**
> Is it going to be in repos? When? Who knows?In Intrepid.

---

### Post by virx on 2008-08-20
2.4.3 came to Hardy although at Hardy release was some earlier version Pidgin.

How do you understand that?
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/259759](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/259759)

---

### Post by bruce89 on 2008-08-20
I might add this to my PPA at some point (I use Empathy now).

---

### Post by picpak on 2008-08-20
> **DougieFresh4U said:**
> Thanks for reply
this is what happened:
dougie@DougiesLeanMachine:~$ sudo dpkg -i libpurple0_2.5.0-1~getdeb1_i386.deb pidgin-data_2.5.0-1~getdeb1_all.deb pidgin_2.5.0-1~getdeb1_i386.deb
[sudo] password for dougie: 
dpkg: error processing libpurple0_2.5.0-1~getdeb1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing pidgin-data_2.5.0-1~getdeb1_all.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing pidgin_2.5.0-1~getdeb1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libpurple0_2.5.0-1~getdeb1_i386.deb
 pidgin-data_2.5.0-1~getdeb1_all.deb
 pidgin_2.5.0-1~getdeb1_i386.deb
dougie@DougiesLeanMachine:~$

Did you download them to your desktop? If so, do

```
cd Desktop/
sudo dpkg -i libpurple0_2.5.0-1~getdeb1_i386.deb pidgin-data_2.5.0-1~getdeb1_all.deb pidgin_2.5.0-1~getdeb1_i386.deb
```

---

### Post by bruce89 on 2008-08-20
> **picpak said:**
> Did you download them to your desktop? If so, do

```
cd Desktop/
sudo dpkg -i libpurple0_2.5.0-1~getdeb1_i386.deb pidgin-data_2.5.0-1~getdeb1_all.deb pidgin_2.5.0-1~getdeb1_i386.deb
```

Therein lies (part of the) problem with GetDeb.

---

### Post by LookTJ on 2008-08-20
> **bruce89 said:**
> Therein lies (part of the) problem with GetDeb.Not really GetDeb, but it is Firefox's default to save files to the desktop.:)

---

### Post by bruce89 on 2008-08-20
> **Taylor said:**
> Not really GetDeb, but it is Firefox's default to save files to the desktop.:)

I meant the fact that you have to download binary packages manually and install them manually.

---

### Post by NWAdawg on 2008-08-20
Installed Pidgin2.5 today. I really like the new custom icon feature.

---

### Post by DougieFresh4U on 2008-08-20
> **picpak said:**
> Did you download them to your desktop? If so, do

```


sudo dpkg -i libpurple0_2.5.0-1~getdeb1_i386.deb pidgin-data_2.5.0-1~getdeb1_all.deb pidgin_2.5.0-1~getdeb1_i386.deb
```

Sure did, and got the same result
I thank you for your input, but I am still lost on this

---

### Post by picpak on 2008-08-20
> **bruce89 said:**
> I meant the fact that you have to download binary packages manually and install them manually.

I agree, a repository would solve all these problems.

> **DougieFresh4U said:**
> Sure did, and got the same result
I thank you for your input, but I am still lost on this

Are you sure you ran "cd Desktop/"? You didn't include it in your quote. Be sure to run that.

---

### Post by zachtib on 2008-08-20
for those that are having trouble installing, look into useing prevu to build proper debs, I just apt-get source'd pidgin-2.4.3, uupdated to 2.5.0, and rebuilt the debs.

I'm having an odd issue of pidgin 2.5 asking me to confirm the ssl cert everytime I start it up...

---

### Post by zachtib on 2008-08-20
for those that are having trouble installing, look into useing prevu to build proper debs, I just apt-get source'd pidgin-2.4.3, uupdated to 2.5.0, and rebuilt the debs.

I'm having an odd issue of pidgin 2.5 asking me to confirm the ssl cert everytime I start it up...

---

### Post by bruce89 on 2008-08-20
> **zachtib said:**
> for those that are having trouble installing, look into useing prevu to build proper debs, I just apt-get source'd pidgin-2.4.3, uupdated to 2.5.0, and rebuilt the debs.

Probably better to get Intrepid's version, and backport it. That way you benefit from packaging changes.

---

### Post by klange on 2008-08-20
Hmm... Quite nice. They finally fixed my two biggest complaints.

---

### Post by DougieFresh4U on 2008-08-20
> **picpak said:**
> I agree, a repository would solve all these problems.



Are you sure you ran "cd Desktop/"? You didn't include it in your quote. Be sure to run that.

I put it exactly as the code presented, thanks for helping:)

dougie@DougiesLeanMachine:~$ cd Desktop/
dougie@DougiesLeanMachine:~/Desktop$ sudo dpkg -i libpurple0_2.5.0-1~getdeb1_i386.deb pidgin-data_2.5.0-1~getdeb1_all.deb pidgin_2.5.0-1~getdeb1_i386.deb
[sudo] password for dougie: 
dpkg: error processing libpurple0_2.5.0-1~getdeb1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing pidgin-data_2.5.0-1~getdeb1_all.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing pidgin_2.5.0-1~getdeb1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libpurple0_2.5.0-1~getdeb1_i386.deb
 pidgin-data_2.5.0-1~getdeb1_all.deb
 pidgin_2.5.0-1~getdeb1_i386.deb
dougie@DougiesLeanMachine:~/Desktop$

---

### Post by LookTJ on 2008-08-20
Hmm where did you actually save the packages? Just out of curiosity. :)

---

### Post by bjschuma on 2008-08-20
> **picpak said:**
> Would that script still try to run when Pidgin isn't, though? I know my AWN script tries to.

I haven't checked, but it probably would still be running even if Pidgin isn't.

---

### Post by zachtib on 2008-08-20
> **bruce89 said:**
> Probably better to get Intrepid's version, and backport it. That way you benefit from packaging changes.

oh, cool, when I built, it wasn't in intrepid yet, time to rebuild

---

### Post by zachtib on 2008-08-20
> **picpak said:**
> FINALLY!

Up next: plugin to set your personal message to the music you're playing. Then I might switch back...

there's pidgin-musictracker, but i've had no luck getting it to work with banshee-1.2

---

### Post by FuturePilot on 2008-08-20
> **zachtib said:**
> there's pidgin-musictracker, but i've had no luck getting it to work with banshee-1.2

This should work.
[http://ubuntuforums.org/showpost.php?p=5140193&postcount=304]("http://ubuntuforums.org/showpost.php?p=5140193&postcount=304")

---

### Post by DougieFresh4U on 2008-08-20
> **Taylor said:**
> Hmm where did you actually save the packages? Just out of curiosity. :)

Desktop

---

### Post by picpak on 2008-08-20
> **DougieFresh4U said:**
> Desktop

What you can do is, if all else fails, open up a terminal and run

```
sudo dpkg -i 
```

drag and drop the three debs (pidgin, pidgin-data, libpurple0) one at a time into the terminal, and hit enter. That should install them. :)

---

### Post by jasmuz on 2008-08-21
Hello to all!

I just installed the pidgin 2.5.0 deb packages from getdeb and im having an issue, maybe you can shine some light on it.

I use 2 Windows Live accounts, one with an @hotmail.com address (no issue here), and another with an @gmail.com address on wich i have a passport enabled, this under the old MSNP9, in Pidgin-Kopete-aMSN and such, runs properly, but under the new and improved MSNP15 screams the following error:

Windows Live ID authentication:Invalid response

Any ideas? 

PS: under the Pidgin 2.4.3 with the MSN-Pecan for WLM, it used to work also.
Please help me out, im stumbling in the dark here.


SOLVED: The issue was, that my non hotmail account wasnt validated under the newer Windows Live ID, instead of MSN Passport. Once i did the logon and accepted the terms, it worked right away.

---

### Post by DougieFresh4U on 2008-08-21
Ok, for some reason I found the files in temp folder. Pref. are set to download to desktop, but any ways, they are in temp. So how do I get them to install from temp, please?

---

### Post by ELD on 2008-08-21
Trust the Pidgin devs to make a really crap way to update your status. Galaxium messenger all the way for MSN.

---

### Post by Polygon on 2008-08-21
how is it bad? you update your status in the same place you update your away message and all that for every other protocol, the thing at the bottom of the buddy list. If you want a personal message, simply select 'available' and type a message. done. If thats too complicated for you, then i'm sorry.

---

### Post by ELD on 2008-08-21
Why should i have to set a status for it though?
They should just have a simple box in plain view to update status. Pidgin devs always seem to do things wierdly.

---

### Post by klange on 2008-08-21
> **ELD said:**
> Why should i have to set a status for it though?
They should just have a simple box in plain view to update status. Pidgin devs always seem to do things wierdly.

Why would they screw up the entire interface for a single protocol?

---

### Post by SomeGuyDude on 2008-08-21
Getting the same "authentication invalid" thing. I can't connect to MSN now. Awesome.

---

### Post by klange on 2008-08-21
> **SomeGuyDude said:**
> Getting the same "authentication invalid" thing. I can't connect to MSN now. Awesome.

Is your account registered as a Passport or a Live account?
All's well here.

---

### Post by Polygon on 2008-08-21
msn also works fine here.

and that box thing at the bottom IS your status. It makes perfect sense to me.

---

### Post by DougieFresh4U on 2008-08-21
I guess I will have to wait it out.
I go have AIM & Kopete I can use

---

### Post by Polygon on 2008-08-21
your a good man. I loved the AIM 5.x.xxxx series of clients for windows, when that AIM 6 crap came out, i was turned off highly.

but now pidgin has come into my life and i haven't looked back =P

---

### Post by ntetreau on 2008-08-22
Just backported the latest Intrepid version of Pidgin using [Prevu]("https://wiki.ubuntu.com/Prevu") , no problems so far.

---

### Post by hufferd on 2008-08-22
> **RATM_Owns said:**
> GetDeb.net has .debs for it: [http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

yay new pidgin

---

### Post by anlag on 2008-08-22
The custom smileys are nice, however it seems when someone sends me a custom smiley, Pidgin overrides that with the fairly ugly Pidgin defaults smileys if they have the same shortcut (:D, :) etc). The only way I found to turn off default smileys was to turn off customs as well. Is there a way to make the other users custom smileys show in place of Pidgin's defaults?

---

### Post by dragonx on 2008-08-22
I had a problem when compiling pidgin

tengo un problema al compilarlo, me dice:
gntaccount.o: In function `add_protocol_options':
/home/dragonx/Desktop/pidgin-2.5.0/finch/gntaccount.c:433: undefined reference to `g_assertion_message'
gntaccount.o: In function `save_account_cb':
/home/dragonx/Desktop/pidgin-2.5.0/finch/gntaccount.c:221: undefined reference to `g_assertion_message'
collect2: ld returned 1 exit status
make[3]: *** [finch] Error 1
make[3]: Leaving directory `/home/dragonx/Desktop/pidgin-2.5.0/finch'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dragonx/Desktop/pidgin-2.5.0/finch'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dragonx/Desktop/pidgin-2.5.0'
make: *** [all] Error 2

what can I do?

---

### Post by b3n87 on 2008-08-23
> **dragonx said:**
> I had a problem when compiling pidgin

tengo un problema al compilarlo, me dice:
gntaccount.o: In function `add_protocol_options':
/home/dragonx/Desktop/pidgin-2.5.0/finch/gntaccount.c:433: undefined reference to `g_assertion_message'
gntaccount.o: In function `save_account_cb':
/home/dragonx/Desktop/pidgin-2.5.0/finch/gntaccount.c:221: undefined reference to `g_assertion_message'
collect2: ld returned 1 exit status
make[3]: *** [finch] Error 1
make[3]: Leaving directory `/home/dragonx/Desktop/pidgin-2.5.0/finch'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dragonx/Desktop/pidgin-2.5.0/finch'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dragonx/Desktop/pidgin-2.5.0'
make: *** [all] Error 2

what can I do?

Hey, just get it from getdeb.net

[http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin)

Its easier to install and a preferred way of installing a package compared to compiling from source.

---

### Post by Starlight on 2008-08-23
Hi! I have a problem with custom smileys on MSN in the new Pidgin. When a person sent me an animated one, I tried to add it, but it just didn't appear on my smiley list. I tried it a few times, and it was the same. And when someone sent me a different one, it got added to the list, but the animation was frozen... it was supposed to be an animated smiley, but only one frame got added to Pidgin. The same smileys work without any problems in aMSN and emesene. Does anyone else have such problems in Pidgin 2.5? :)

---

### Post by klange on 2008-08-23
> **Starlight said:**
> Hi! I have a problem with custom smileys on MSN in the new Pidgin. When a person sent me an animated one, I tried to add it, but it just didn't appear on my smiley list. I tried it a few times, and it was the same. And when someone sent me a different one, it got added to the list, but the animation was frozen... it was supposed to be an animated smiley, but only one frame got added to Pidgin. The same smileys work without any problems in aMSN and emesene. Does anyone else have such problems in Pidgin 2.5? :)

The animated emotes are probably not supported yet on the client side in Pidgin - it's a new feature, hacked together through GSoC, and it has a number of bugs.

---

### Post by fornix on 2008-08-23
>  
FINALLY!

Up next: plugin to set your personal message to the music you're playing. Then I might switch back...
Try Musictracker [http://code.google.com/p/musictracker/]("http://code.google.com/p/musictracker/")
I wouldn't have used pidgin without it!

---

### Post by Starlight on 2008-08-23
> **WindowsSucks said:**
> The animated emotes are probably not supported yet on the client side in Pidgin - it's a new feature, hacked together through GSoC, and it has a number of bugs.

ok, thanks for the reply :) I hope they fix it soon... Pidgin is cool, but without a good custom smileys support, it's not as good as aMSN or emesene when it comes to the MSN network.

---

### Post by Sammi on 2008-08-23
Nobody gets to choose what IM protocol they use, cause you have to use the same one that the people you want to chat with use. Where I live everybody uses MSN, so that's what I use too.

I moved to Emesene immediately after it was released, because it had much better MSN support, but this update might bring me back to Pidgin. At least I'm going to give it a try again.

Got the debs from getdeb.net, and it installed and ran without troubles. Looking forward to seing if it will suit my needs.

---

### Post by RiceMonster on 2008-08-23
> **Sammi said:**
> Nobody gets to choose what IM protocol they use, cause you have to use the same one that the people you want to chat with use. Where I live everybody uses MSN, so that's what I use too.

I moved to Emesene immediately after it was released, because it had much better MSN support, but this update might bring me back to Pidgin. At least I'm going to give it a try again.

Got the debs from getdeb.net, and it installed and ran without troubles. Looking forward to seing if it will suit my needs.

Yeah, once this version makes it into the Arch repositories, I'm going to give it a try. I don't want to compile from source. I also use pidgin

---

### Post by khc on 2008-08-24
> **WindowsSucks said:**
> The animated emotes are probably not supported yet on the client side in Pidgin - it's a new feature, hacked together through GSoC, and it has a number of bugs.

Please don't spread misinformation. While custom emoticons is a new feature, it's not done as part of GSoC at all.

---

### Post by DougieFresh4U on 2008-08-24
I am really frustrated trying to install this pidgin.
I down;oad the pidgin file but installer tells me dependency problem with libpurple, so I try to install libpurple and it tells me dependency problem with libperl5.8. 
I installed the Prevu hoping to go that route to install pidgin bu I am kind of lost on what to do next.
Could some one please give it a go 
Thanks

---

### Post by klange on 2008-08-24
> **khc said:**
> Please don't spread misinformation. While custom emoticons is a new feature, it's not done as part of GSoC at all.
I must be mistaken, then, I thought all the MSN enhancements were run through SoC.

---

### Post by ]FT[ on 2008-08-24
> **DougieFresh4U said:**
> I am really frustrated trying to install this pidgin.
I down;oad the pidgin file but installer tells me dependency problem with libpurple, so I try to install libpurple and it tells me dependency problem with libperl5.8. 
I installed the Prevu hoping to go that route to install pidgin bu I am kind of lost on what to do next.
Could some one please give it a go 
Thanks

If you're using Ubuntu Intrepid Ibex, you will not be able to install Pidgin 2.5 via the packages for Hardy Heron, because those packages depends on Perl 5.8, and on Intrepid Ibex there's Perl 5.10, and you can't have both of them installed. The simplest thing to do is to compile it from sources, or modify the dependancies of the packages (and this is what I did). If you want I can spread with you the modified packages:

[pidgin_2.5.0-1~getdeb1-hacked_i386.deb]("http://www.deadware.org/ubuntu/pidgin_2.5.0-1%7Egetdeb1-hacked_i386.deb")
[pidgin-data_2.5.0-1~getdeb1_all.deb]("http://www.deadware.org/ubuntu/pidgin-data_2.5.0-1%7Egetdeb1_all.deb")
[libpurple0_2.5.0-1~getdeb1-hacked_i386.deb]("http://www.deadware.org/ubuntu/libpurple0_2.5.0-1%7Egetdeb1-hacked_i386.deb")

Let me know if they work.
R

EDIT: However, if I could help you, you should install them putting all the three packages in one new empty folder (maybe "pidgin" in your home dir), than:
- open a terminal
- cd ~/pidgin
- sudo dpkg -i *.deb
It is the easyiest way to install programs which uses more than one deb file.

---

### Post by DougieFresh4U on 2008-08-24
Thanks so much for your help. I think it worked
I have included a screenshot About and if it is correct version let me know please.
Thanks so much again

---

### Post by super.rad on 2008-08-24
If your using Intrepid Ibex just make sure you have all updates installed, just did a fresh install of Intrepid and installed all upgrades and I'm now using pidgin 2.5

---

### Post by hufferd on 2008-08-25
I don't know if I will up date just yet ...  I assume that when pidgin 2.5 is in the repos that my install will update it self correct?

---

### Post by &gt;.3 on 2008-08-25
So I compiled it 
```
sudo apt-get install build-essential network-manager-dev
sudo apt-get build-dep pidgin
tar jxvf pidgin-2.5.0.tar.bz2
cd pidgin-2.5.0
./configure &#8211;enable-gnutls=yes
make && sudo make install
```
Right.
But it won't start. When i click on the pidgin icon all it does is [THIS]("http://img261.imageshack.us/img261/6577/screenshotlh8.png") for a few seconds and then nothing.
What's going on there? Help, plz.

---

### Post by 5m0k3 on 2008-08-25
> **>.3 said:**
> So I compiled it 
```
sudo apt-get install build-essential network-manager-dev
sudo apt-get build-dep pidgin
tar jxvf pidgin-2.5.0.tar.bz2
cd pidgin-2.5.0
./configure &#8211;enable-gnutls=yes
make && sudo make install
```
Right.
But it won't start. When i click on the pidgin icon all it does is [THIS]("http://img261.imageshack.us/img261/6577/screenshotlh8.png") for a few seconds and then nothing.
What's going on there? Help, plz.

Open pidgin via the terminal (by typing "pidgin" [without the quotes]) and note any errors or other feedback

---

### Post by anlag on 2008-08-25
> **WindowsSucks said:**
> The animated emotes are probably not supported yet on the client side in Pidgin - it's a new feature, hacked together through GSoC, and it has a number of bugs.

Animated smileys are supported at least to some extent. I've added two of them: one a pair of clapping hands, which work only they clap bloody fast, and the other a smiley waving a Leeds United scarf (mighty whites!) over his head - which works perfectly.

---

### Post by meho_r on 2008-08-29
Did anyone experience any problems with files sending (MSN protocol)? Can't send and can't receive a thing :(

---

### Post by Johnsie on 2008-08-29
When is this going to be in the hardy repositories? Or do we have to wait months to get up-to-date software?

---

### Post by RiceMonster on 2008-08-29
> **Johnsie said:**
> When is this going to be in the hardy repositories? Or do we have to wait months to get up-to-date software?

You'll probably have to wait to untill Ibex, unfortunately.

---

### Post by Johnsie on 2008-08-29
That sucks... If I install it from getdeb.net will I have to update manually every time there's an update to pidgin or will Ubunbtu know when the official Ubuntu version is more recent than the getdeb one?

---

### Post by bruce89 on 2008-08-29
> **Johnsie said:**
> That sucks... If I install it from getdeb.net will I have to update manually every time there's an update to pidgin

Yes. Therein lies one of the problems with GetDeb.

---

### Post by Johnsie on 2008-08-29
And installing an external deb iis a big security risk too... Because you give root access to the package and the package could contain nasty things. Grrr...

---

### Post by RiceMonster on 2008-08-29
Yeah, thats one of the things I don't like about Ubuntu; the "frozen" repos.

---

### Post by Polygon on 2008-08-29
> **Johnsie said:**
> That sucks... If I install it from getdeb.net will I have to update manually every time there's an update to pidgin or will Ubunbtu know when the official Ubuntu version is more recent than the getdeb one?

unless pidgin releases incremental updates, like 2.4.1, ubuntu will never update pidgin, because introducing major ugrapdes into the repos without proper testing could lead to instability.

and also, depends on the upgrade. Like usually packages are like pidgin-data-2.5.0getdeb, but if a update comes along for pidgin 2.6, then it will upgrade correctly.

---

### Post by napalm brain on 2008-08-29
I like manually updgrading because I feel like a bad ***. This is due in part to me being absolutely clueless on how to do above basic commands. I follow a guide and update everything in the terminal. It makes me feel good.

BTW, the new Pidgin looks great. Much more glossy. And should I say.. sexy?

---

### Post by brunomiguel on 2008-08-30
I've installed Pidgin 2.5.0 successfully with the usual 'sudo ./configure; sudo make; sudo make install' (all my sources go to /usr/src), but when I try to create a deb package with 'sudo checkinstall -D', I get this error:

[B]test -z "/usr/local/share" || /bin/mkdir -p "/usr/local/share"
 /bin/bash /usr/src/pidgin-2.5.0/install-sh -c -m 644 'icons/hicolor/16x16/apps/pidgin.png' '/usr/local/share/icons/hicolor/16x16/apps/pidgin.png'
chmod: a mudar as permissões de `/usr/local/share/icons/hicolor/16x16/apps/_inst.13993_': Ficheiro ou directoria inexistente
 /bin/bash /usr/src/pidgin-2.5.0/install-sh -c -m 644 'icons/hicolor/22x22/apps/pidgin.png' '/usr/local/share/icons/hicolor/22x22/apps/pidgin.png'
chmod: a mudar as permissões de `/usr/local/share/icons/hicolor/22x22/apps/_inst.13999_': Ficheiro ou directoria inexistente
 /bin/bash /usr/src/pidgin-2.5.0/install-sh -c -m 644 'icons/hicolor/24x24/apps/pidgin.png' '/usr/local/share/icons/hicolor/24x24/apps/pidgin.png'
chmod: a mudar as permissões de `/usr/local/share/icons/hicolor/24x24/apps/_inst.14005_': Ficheiro ou directoria inexistente
 /bin/bash /usr/src/pidgin-2.5.0/install-sh -c -m 644 'icons/hicolor/32x32/apps/pidgin.png' '/usr/local/share/icons/hicolor/32x32/apps/pidgin.png'
chmod: a mudar as permissões de `/usr/local/share/icons/hicolor/32x32/apps/_inst.14011_': Ficheiro ou directoria inexistente
 /bin/bash /usr/src/pidgin-2.5.0/install-sh -c -m 644 'icons/hicolor/48x48/apps/pidgin.png' '/usr/local/share/icons/hicolor/48x48/apps/pidgin.png'
chmod: a mudar as permissões de `/usr/local/share/icons/hicolor/48x48/apps/_inst.14017_': Ficheiro ou directoria inexistente
make[4]: *** [install-nobase_dist_pidginiconsDATA] Error 1
make[4]: Leaving directory `/usr/src/pidgin-2.5.0/pidgin/pixmaps'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/usr/src/pidgin-2.5.0/pidgin/pixmaps'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/src/pidgin-2.5.0/pidgin/pixmaps'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/pidgin-2.5.0/pidgin'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.[/B]


The reason I want to create a deb package is because I want to install pidgin-extprefs, pidgin-guifications, pidgin-libnotify, pidgin-otr and they all install the pidgin package from the repos. I know I could just download the plugins source and compile them, but I want to avoid it.

---

### Post by coolbrook on 2008-08-30
Thanks for the notification.  Updated.

---

### Post by picpak on 2008-08-30
> **bruce89 said:**
> Yes. Therein lies one of the problems with GetDeb.

Try Pidgin's PPA:

[https://launchpad.net/~pidgin-developers/+archive](https://launchpad.net/~pidgin-developers/+archive)

---

### Post by gardara on 2008-08-31
2.5.1 out now! You can get it from getdeb [http://www.getdeb.net/release/3140](http://www.getdeb.net/release/3140)

---

### Post by drubin on 2008-08-31
> **gardara said:**
> 2.5.1 out now! You can get it from getdeb [http://www.getdeb.net/release/3140](http://www.getdeb.net/release/3140)

What changes/bug fixes? Is it worth upgrading my one seems to be behaving not one crash.

---

### Post by LookTJ on 2008-08-31
> **rubinboy said:**
> What changes/bug fixes? Is it worth upgrading my one seems to be behaving not one crash.
[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

---

### Post by drubin on 2008-08-31
I am going to give it a few days encase they find any other little bugs :)

---

### Post by wipeout140 on 2008-08-31
> **rubinboy said:**
> What changes/bug fixes? Is it worth upgrading my one seems to be behaving not one crash.

[B]Version 2.5.1 ( 08/31/2008 )

[/B][View all closed tickets for this release.]("http://developer.pidgin.im/query?status=closed&milestone=2.5.1") 
 
[LIST]
[*]**libpurple**
[LIST]
[*]In the Join/Part plugin, add the ability to apply the rules to buddies. By default, joins and parts for buddies are still shown.
[*]Support SOCKS proxies specified in GNOME or Windows proxy settings.
[*]Fix some possible crashes in MSNP15.
[*]Enable a default SSL trust relationship for MSN servers.
[*]Avoid disconnecting from XMPP servers on parse errors that are non-fatal.
[*]Include some perl files that were mistakenly omitted in 2.5.0.
[/LIST]
 
[/LIST]

[LIST]
[*]**Pidgin**
[LIST]
[*]Prevent use of custom smilies without "shortcuts."
[*]Fix a crash that could appear with AIM buddy tooltips.
[/LIST]
 
[/LIST]
**Artwork** 
[LIST]
[*]General refresh of many icons in the interface.
[*]Many cleanups to artwork source are now included in the distribution.
[*]A new "throbber" animation has been added to indicate when accounts are connecting.
[/LIST]

---

### Post by SilverDragon on 2008-08-31
> **picpak said:**
> Try Pidgin's PPA:

[https://launchpad.net/~pidgin-developers/+archive](https://launchpad.net/~pidgin-developers/+archive)

Thanks, I was looking for this.

---

### Post by tuchki on 2008-08-31
Hi. i've installed pidgin 2.5 but i didn't uninstall pidgin 2.4.1. then when i'm using pidgin, it closes when i hit enter to send a message, sometimes i can send some but others i can not send anything. even sometimes it closes inmediately. i've tried to uninstall pidgin and start again. i tried with sudo apt-get remove pidgin pidgin-data sudo apt-get autoremove and i deleted /home/user/.pidgin folder. but i cant make that pidgin works correctely.

i've tried with .deb and compiling... now i tried with pidgin 2.5.1 but i have the same problem. i have a backtrace but it has "??" where the function's name has to be. 

does anybody knows if there is a way to erase everithing about pidgin and start again?

thank you

---

### Post by garg on 2008-09-09
Does any one know why if I type pidgin --version then it says 2.5.1 but if I type pidgin and then go to Help > About > It shows Pidgin 2.4.1 ?


edit: nevermind. I completely removed pidgin and then reinstalled from source and now it shows 2.5.1

---

### Post by merlos on 2008-09-10
Hi all guys.
I tried pidgin 2.5.0 and everything is ok.

The only problem I noticed is related to Custom Smilies. 
When I try to add a Smile from a chat with some of my contact (right button -> add custom smile ) this won't work.

The log show me that pidgin miss **custom_smiley** directory on my profile dir

```
(11:08:31) gtksmiley: adding a new smiley
(11:08:31) util: Writing file /home/merlos/.purple/custom_smiley/8ae92b4f24d59aeace2d4b817fb9cf1a022790e3.png
(11:08:31) util: _Error opening file /home/merlos/.purple/custom_smiley_/8ae92b4f24d59aeace2d4b817fb9cf1a022790e3.png.save for writing: Nessun file o directory
(11:08:31) smileys: Error reading /home/merlos/.purple/custom_smiley/8ae92b4f24d59aeace2d4b817fb9cf1a022790e3.png: Apertura del file "/home/merlos/.purple/custom_smiley/8ae92b4f24d59aeace2d4b817fb9cf1a022790e3.png" fallita: Nessun file o directory
(11:08:32) util: Writing file prefs.xml to directory /home/merlos/.purple
(11:08:32) util: Writing file /home/merlos/.purple/prefs.xml
```

I solved the problem creating this dir, and now I can add custom smilies and use it.

```
mkdir ~/.purple/custom_smiley
```

Hope this help someone with the same problem

Giovanni
:)

---

### Post by hazze_h on 2008-09-15
> **SomeGuyDude said:**
> Getting the same "authentication invalid" thing. I can't connect to MSN now. Awesome.

I had the same error with 2.5.0.
I solved it by logging into [https://login.live.com](https://login.live.com) and accepted the agreement.
Then it was possible to use pidgin with msn again.

/Hazze

---

### Post by boobuntu on 2008-09-15
pidgin rox0rs my s0xors.

---

### Post by RayVad on 2008-10-18
Working here!

First, uninstall the old Pidgin, pidgin-data and libpurple0

New installation done like this:

1) Download files to desktop from [http://www.getdeb.net/release/3140](http://www.getdeb.net/release/3140)

2a) in terminal do: *sudo dpkg -i libpurple0_2.5.1-1~getdeb1_i386.deb pidgin-data_2.5.1-1~getdeb1_all.deb pidgin_2.5.1-1~getdeb1_i386.deb*
or
2b) Alternatively you can do in a terminal: *sudo dpkg -i* and drag every file in it and hit enter.

3) In both situations you will get dependency errors, so open a new terminal and do:  *sudo apt-get install -f*
   This will continue the installation for both the dependencies and .deb files.

Greetz,
Ray

---

### Post by virx on 2008-10-28
Can Pidgin change status to busy automatically, when I open full screen application - like msn messenger does?

---

### Post by Hubris2 on 2008-11-03
For those running Intrepid, what package from the repos do you have installed?  I have 1.2.5.2-Oubuntu1, but I only have Pidgin 2.0 installed.  Verified by running pidgin --version.

---

### Post by Polygon on 2008-11-03
> **virx said:**
> Can Pidgin change status to busy automatically, when I open full screen application - like msn messenger does?

its certainly possible, but it requires the application(s) that are going fullscreen to send a dbus command to pidgin or w/e so it automatically sets you away/busy or something. Make a wishlist bug for the program =)

and on intrepid im running the latest version from the repos, 2.5.2 i think

---

### Post by FuturePilot on 2008-11-03
> **Hubris2 said:**
> For those running Intrepid, what package from the repos do you have installed?  I have 1.2.5.2-Oubuntu1, but I only have Pidgin 2.0 installed.  Verified by running pidgin --version.

Did you compile Pidgin yourself at any point? You may actually have two versions installed and your executing the old one.

---

### Post by Old Marcus on 2008-11-03
Getting an error on configure:
```

configure: error: GNU gettext tools not found; required for intltool

```
Also, I can't find package networkmanager-dev. Does anyone know where I can get it?

---

### Post by Hubris2 on 2008-11-03
It is possible I manually-compiled version 2.0 back when it first came out.  What is the 'correct' way of uninstalling an old version of an app that's been compiled from source?  I assume there's something more complete than simply renaming the executable?

> **FuturePilot said:**
> Did you compile Pidgin yourself at any point? You may actually have two versions installed and your executing the old one.

---

