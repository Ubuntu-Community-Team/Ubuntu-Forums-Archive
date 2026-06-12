---
title: "getting started with apparmor"
date: 2012-10-28
forum: Security
---

### Post by mike acker on 2012-10-28
it is my considered opinion that it is not un-reasonable for a system owner/operator to inquire regarding the actual activity of an installed application program

from reading some of our notes here it appears that the AppArmor log is the place to look.

to get to the AppArmor log a profile for the application to be monitored will be needed

accordingly I've made an attempt to learn how this should be done; sadly I seem to be on the wrong track somehow...

I would like to generate a profile for the application program "Audacious".  Here's how I tried to do it:
```

ackerwaa@acker4:/usr/bin$ sudo /etc/init.d/genprof audacious
sudo: /etc/init.d/genprof: command not found

ackerwaa@acker4:/usr/bin$ sudo /etc/init.d/apparmor genprof audacious
Usage: /etc/init.d/apparmor {start|stop|restart|reload|force-reload|status|recache}

```I'm thinking it looks like I'm working from dated documentation...

do we have any updated notes on Getting Started using AppArmor ?

---

### Post by Hungry Man on 2012-10-28
Make sure you have the package apparmor-utils installed and then you can use the command:

aa-genprof audacious

or

aa-autodep audacious

You can also see the sticky at the top of this subforum for details and information.

---

### Post by mike acker on 2012-10-28
> **Hungry Man said:**
> Make sure you have the package apparmor-utils installed and then you can use the command:

aa-genprof audacious

or

aa-autodep audacious

You can also see the sticky at the top of this subforum for details and information.

well, that helped.  i issued
```

sudo apt-get install apparmor-utils

```and it installed a bunch of stuff...

after that, i ussued:
```

sudo aa-genprof audacious

```which resulted in
```

Writing updated profile for /usr/bin/audacious.
Setting /usr/bin/audacious to complain mode.

Before you begin, you may wish to check if a
profile already exists for the application you
wish to confine. See the following wiki page for
more information:
http://wiki.apparmor.net/index.php/Profiles

Please start the application to be profiled in 
another window and exercise its functionality now.

Once completed, select the "Scan" button below in 
order to scan the system logs for AppArmor events.  

For each AppArmor event, you will be given the  
opportunity to choose whether the access should be  
allowed or denied.

Profiling: /usr/bin/audacious

[(S)can system log for AppArmor events] / (F)inish
Setting /usr/bin/audacious to enforce mode.
Reloaded AppArmor profiles in enforce mode.

Please consider contributing your new profile! See
the following wiki page for more information:
http://wiki.apparmor.net/index.php/Profiles

Finished generating profile for /usr/bin/audacious.

```this is clearly effective: I didn't "get it" as far as running the app with the gen-profile in progress... so I just selected "finish" immediately.  that locked out the app, period.

I've run into a problem though: I'm using an admin account -- which has sudo authority. apparmor commands must be run with sudo: i tried them plain but they were failed

my "user account" -- does not have sudo authority

so i think i have to assign sudo authority to my user account -- perhaps temporarily and then re-do the profile generation

I was able to set the profile to "complain" mode
```

sudo aa-complain audacious
Setting /etc/apparmor.d/usr.bin.audacious to complain mode.

```and after that I was able to use audacious in my user account again.  

i should now be able to "tail" the log...... and thus to learn what activity this program like to participate in

in terms of the actual app -- audacious -- it will need access to the music library -- which is in my user account -- so i may have to run the profile gen from my user account

let me know if you have any more hints | clues for me !!

thanks for the help!!

---

### Post by cariboo on 2012-10-28
You should actually create an apparmor profile for an application that connects to the internet, I just tried audacious, and using:

```
sudo lsof -i -P -n
```

I don't see any outgoing connections.

I'd suggest Rhythmbox, as it goes out and looks for cover art by default.

---

### Post by mike acker on 2012-10-28
> **cariboo907 said:**
> You should actually create an apparmor profile for an application that connects to the internet, I just tried audacious, and using:

```
sudo lsof -i -P -n
```I don't see any outgoing connections.

I'd suggest Rhythmbox, as it goes out and looks for cover art by default.

OK, I dug up some documentation on "lsof": list open files.  This would be an easy way to check an app for internet activity, -- but -- it's going to give a system/current condition type report.  from a security standpoint we are interested in files that were opened at one time.... which might be subsequently closed and not show in the point in time report.
~~~

Electronic Privacy is a hot-button issue for me.  From a security standpoint one concern that I think merits attention is the question: what information is my system exfiltrating about me? this, simply because we all know: there are both good guys and bad guys "out there".

---

### Post by cariboo on 2012-10-28
If you are interested in what data is going in an out of your system, have a look at wireshark, it's in the repositories.

To set it up so that you don't have to run wireshark as root, have a look [here]("http://askubuntu.com/questions/74059/how-do-i-run-wireshark-with-root-privileges")

---

### Post by mike acker on 2012-10-28
> **cariboo907 said:**
> If you are interested in what data is going in an out of your system, have a look at wireshark, it's in the repositories.

To set it up so that you don't have to run wireshark as root, have a look [here]("http://askubuntu.com/questions/74059/how-do-i-run-wireshark-with-root-privileges")

I'm definitely going to do that. I'm still a terrible newbee though:(

The sort of tools we are working with here -- are the reason I wanted to switch to Linux.  With a Windows system -- we have no clue as to what the machine is actually doing:(

I managed to generate a profile for Audacious. I have it set in COMPLAIN mode; I'll check the log tomorrow to see how I did. Hopefully any issues will be related to directories to be accessed,--
~~~~~~~~~~~
Amendment:
after installing (above utility pack) I noticed I now have a profile for Firefox although it's not active yet

as we know browsers and e/mail are principle attack vectors. 

should Ubuntu come standard with Firefox and Thunderbird confined?

AppArmor reminds me of RACF: you had to have permission for everything,-- not only the directories you wanted to update -- but what program you could use to work with .  The PC movement gleefully blew this concept out the back door.... with.... [what should have been predictable results.]("http://www.scmagazine.com.au/News/320952,hackers-steal-over-75-percent-of-south-carolina-social-security-numbers.aspx")

---

### Post by mike acker on 2012-10-29
the biggest problem i'm running into is all the out of date documentation

e.g. where does apparmor log to and how do i clear that log out ?

```

sudo aa-logprof

```seemed to find and analyze the log including offering me a chance to authorize exceptions but I didn't understand the glob thing at all
~~~~~~~~~~~~
Guide to Apparmor

Objective: to apply containment to an application

1. make sure you are sudo authorized
    sudo adduser <username> sudo

    that will allow you to execute the commands you need
    you can remove yourself later

2. select an app . Make sure it is stopped

3. sudo aa-genprof <app name>
    leave this open
    run your app . Perform you usual activities. 
    close the app 
    go back and close the aa-genprof
    this will create a profile and put you in fail mode

4. sudo aa-complain <app name>
    this will put the profile in complain mode so you can test it

5. testing
    run you app, &#8220;Do your thing&#8221;, and close it
    sudo aa-logprof <app name>
    this will scan the apparmor log for your app and suggest changes. 
    Just OK everything; this critter is pretty esoteric.
    sudo gedit /etc/apparmor.d/<profile name>
    
    you want to list the directory of /etc/apparmor.d
    and pick out your profile name which uses . in place of /
    
    correct the profile and save it

6. sudo /etc/init.d/apparmor reload

    this will reload the profiles

7. go back to step 5 until you are happy with the log test

8. sudo aa-enforce <profile>
    if the app konks out go back to step 4

END

---

### Post by rookcifer on 2012-10-30
Apparmor logs to syslog.

---

### Post by mike acker on 2012-11-01
it would appear that an AppArmor  profile for FIREFOX
written by Jamie Strandboge (Canonical) is provided with the system

I've enabled it and put it into COMPLAIN mode

I think getting FIREFOX and THUNDERBIRD into AppArmor should be
just about an important first step in Security

From what I know of malware confining these two programs will be more effective v. malware than A/V

A/V is always a day late..... after the fact. and is getting better and better at ducking A/V scanners.  In the end: you can't scan for something if you don't know what it looks like. And polymorphic malware is constantly changing

watching program behavior should always work though: I don't care who you are you ain't updating SYSRES.

It is probably the case that both T-Bird and F-Fox should be distributed in active AppArmor profiles

a Secondary Risk is also present though: If I cut& Paste from a web page into a LibreOffice .odt  document.... i could transport a virus that way. Within Linux such a virus would not be able to update the kernel.

there remains the question then: could a script, working from LibreOffice install a plug-in and create a MITM attack within FireFox?  The thing to do would be to put LibreOffice into AppArmor and then DENY access to --- whereever FireFox keeps the data that initiates a plug-in .

I am not going to activate Flash in my firefox until after the profile passes service testing.
~~~~~~~~~~~~~~

amendment
here is a little tid bit from a pdf from Sophos circulated today via Network World. regarding "ZeroAccess" dropper:
> ZeroAccess droppers have changed as the rootkit itself has evolved. Currently, droppers
are usually obfuscated using complex polymorphic packers, software designed to modify
the appearance of a program so that no two instances look the same to a security scanner.
These packers are a typical example of the protection measures that modern malware
employs to both hinder analysis and to avoid detection by security tools. They add layers
of compression and encryption to a program to conceal its true purpose. They are updated
several times a day and are always checked against anti-malware scanners before they are
released into the wild.
This, and BlackHole are currently Top Threats.  Both attack via the browser, or via an e/mail that is html formatted or contains links that can direct the intended victim's browser to the attack site

I am running Jamie's Firefox profile in complain mode now; we'll see how it does after a bit.  Also, I just now generated a profile for Thunderbird ( I didn't find one in our downloads :-( )

IMHO(FWIW) if we AppArmor Firefox and Thunderbird we will have block the main attack vectors.  

the remains will be, as I mentioned, snippets that I might Cut&Paste, into (e.g.) LibreOffice and then run -- but without the AppArmor

too, the other Main Attack Vector is PhishBait: e.g. free apps that come with a bonus.  we need to work on gaining a better understanding of the Trust Models that PGP depends on.  that a software package is "signed by the vendor" -- is meaningless -- unless we have a means of authenticating the vendor's signature.

the CA does that you say?  OK, but did you authenticate the CA ?  you don't need to-- because the browser does it?  ok, did you ever look to see how many certificates you have in your browser?

---

