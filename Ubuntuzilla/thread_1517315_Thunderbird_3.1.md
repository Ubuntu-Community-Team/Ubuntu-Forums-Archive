---
title: "Thunderbird 3.1"
date: 2010-06-24
forum: Ubuntuzilla
---

### Post by witeshark17 on 2010-06-24
Installed it today and it won't start; it acts as though there is another copy running. There are no error messages.

---

### Post by pelmenept on 2010-06-24
I already posted there, too lazy to repost

[http://getsatisfaction.com/mozilla_messaging/topics/t_bird_3_1_wont_start?utm_content=topic_link&utm_medium=email&utm_source=reply_notification](http://getsatisfaction.com/mozilla_messaging/topics/t_bird_3_1_wont_start?utm_content=topic_link&utm_medium=email&utm_source=reply_notification)

---

### Post by witeshark17 on 2010-06-24
I see no answer that works in that thread. Did you get a solution?

---

### Post by nanotube on 2010-06-25
thunderbird 3.1 has not yet been released, and thus is not in the ubuntuzilla repositories, which follows official mozilla releases only.

so i recommend you try posting your question in some other section of the forums.

EDIT: oh, i see it /has/ just been released... well i'll push out the update to the repos.

---

### Post by pelmenept on 2010-06-25
No, whiteshark17. I have no solution. Mine is not working. Using Claws for now. and falling back in love with it.

---

### Post by nanotube on 2010-06-25
> **pelmenept said:**
> No, whiteshark17. I have no solution. Mine is not working. Using Claws for now. and falling back in love with it.

it seems that it could be a problem of something in your profile not being liked by tbird3.1

i can suggest moving your profile out of the way (~/.thunderbird and/or ~/.mozilla-thunderbird), and then try starting again. that'll give you a quick test to see if it's a profile problem or not.

---

### Post by witeshark17 on 2010-06-25
> **nanotube said:**
> it seems that it could be a problem of something in your profile not being liked by tbird3.1

i can suggest moving your profile out of the way (~/.thunderbird and/or ~/.mozilla-thunderbird), and then try starting again. that'll give you a quick test to see if it's a profile problem or not. Thanks, I'll have a go at something... I may try the last suggestion in [ my help thread at Mozilla]("http://getsatisfaction.com/mozilla_messaging/topics/t_bird_3_1_wont_start")

Does this command work in the repos?

```
sudo apt-get install thunderbird-3.1 thunderbird-3.1-gnome-support
```

---

### Post by FrancoNero on 2010-06-27
> **witeshark17 said:**
> Thanks, I'll have a go at something... I may try the last suggestion in [ my help thread at Mozilla]("http://getsatisfaction.com/mozilla_messaging/topics/t_bird_3_1_wont_start")

Does this command work in the repos?

```
sudo apt-get install thunderbird-3.1 thunderbird-3.1-gnome-support
```

there is no thunderbird-3.1 in the repos :(

---

### Post by nanotube on 2010-06-27
> **witeshark17 said:**
> Thanks, I'll have a go at something... I may try the last suggestion in [ my help thread at Mozilla]("http://getsatisfaction.com/mozilla_messaging/topics/t_bird_3_1_wont_start")

Does this command work in the repos?

```
sudo apt-get install thunderbird-3.1 thunderbird-3.1-gnome-support
```

depends on the repos. official ubuntu repos - no.
ubuntuzilla repo does have tb3.1

---

### Post by jasmines on 2010-06-27
Hi, I've upgraded from 3.0.4 to 3.1 via ubuntuzilla repo (on Lucid 10.4/Gnome). The bird is running, but my cpu goes soon over 100%, with no particular errors. I've tried the safe mode, and disabled all plugins and extensions, but it was the same...

Can anyone notice the same error?

---

### Post by bvucinic on 2010-06-27
I have installed 3.1 today and it won't start no error messages, no anything ??? I can still run the old 3.0.4 by starting the thunderbird.ubuntu. I've tried reinstalling, removing, manually always with same result the command exits with no messages whatsoever???

---

### Post by bvucinic on 2010-06-27
solution:
remove with ubuntuzilla.
Install deb file from:
[http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.1-0ubuntu1_i386.deb?use_mirror=ovh](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/t/thunderbird-mozilla-build/thunderbird-mozilla-build_3.1-0ubuntu1_i386.deb?use_mirror=ovh)

---

### Post by rzs0502 on 2010-06-28
I've upgrade to TB 3.1 on Arch Linux and experienced the same issue.
Moved all my extensions to a backup directory and it started up fine.
By putting them back one at a time, I found the problem to be my LookOut extension.
( ~/.thunderbird/<profile_id.default>/extenstions/lookout@aron.rubin )
So in my case, this was the cause of the problem

---

### Post by rzs0502 on 2010-06-28
Correction, the problem re-occurred.
If you start TB without any extensions, it runs.
If you start with the Lightning extension, it runs - but with errors on the console.

<code>
Error: Parser Error. Could not find 'VCALENDAR' component in: 
null
Stack: 
1: [file:///home/xxxxxx/.thunderbird/5m7d5sjk.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/modules/calUtils.jsm -> file:///home/rakeshs/.thunderbird/5m7d5sjk.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/calendar-js/calIcsParser.js:91] ip_processIcalComponent
2: [file:///home/xxxxxx/.thunderbird/5m7d5sjk.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/modules/calUtils.jsm -> file:///home/rakeshs/.thunderbird/5m7d5sjk.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/calendar-js/calIcsParser.js:232] parseString_done
3: [file:///home/xxxxxx/.thunderbird/5m7d5sjk.default/extensions/%7Be2fda1a4-762b-4020-b5ad-a41df1933103%7D/modules/calUtils.jsm:165] response_run
</code>

If you close TB and try to re-open, the program will fail to start.
I've tried installing the latest (1.0 beta2) version, but no luck.

---

### Post by FrancoNero on 2010-06-28
nanotube, ubuntuzilla doesn't have 64bit

---

### Post by FrancoNero on 2010-06-28
what's even more frustrating, is that one of the key addons for Thunderbird only works with 3.1 in its latest version

[http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html](http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html)

that makes an available upgrade to 3.1 ond Ubuntu even more essential. How hard is it to supply a .deb 64bit of this application? I just don't understand...

---

### Post by nanotube on 2010-06-28
> **FrancoNero said:**
> what's even more frustrating, is that one of the key addons for Thunderbird only works with 3.1 in its latest version

[http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html](http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html)

that makes an available upgrade to 3.1 ond Ubuntu even more essential. How hard is it to supply a .deb 64bit of this application? I just don't understand...

Hi,
Well, using the approach taken by ubuntuzilla, which is to pack the original mozilla build binaries into a .deb, it is approximately impossible - since mozilla doesn't make 64bit binary releases.

If you want 64bit, you can compile it from mozilla source yourself, or use the mozilla daily builds repo. 

thunderbird-stable repo still only has 3.0.5... so that one is a no-go for now.

---

### Post by FrancoNero on 2010-06-28
what a let-down :(  it's like a turf war among open source software providers, and it's either mozilla who has lots of fun excluding 64bit systems or ubuntu who's having lots of fun not allowing major upgrades within stable releases. as if tb 3.1 would crash ubuntu or something, as if it wouldn't crash enough without thunderbird :P

---

### Post by pmulgaonkar on 2010-07-01
I am having similar problems: since upgrading to 3.1 from ubuntuzilla on a 32 bit ubuntu 9.10, I can start tbird only by first entering safe mode, then restarting. I have to do this each time. Can someone help diagnose this? What info should I submit? The only add on I have is lightning.

Is there a way to revert back to the previous version?

More info: when I run in terminal with safe mode, I get an error message:
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libnullplugin.so [libxul.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so [libxul.so: cannot open shared object file: No such file or directory]

---

### Post by Umang on 2010-07-01
Hi all,

The issue, as discussed on the enigmail forums is because of some permissions issue cause by the ~/.thunderbird -> ~/.mozilla-thunderbird symlink. Running the following commands should help:

```
 $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
 $ unlink ~/.thunderbird
 $ mv ~/.mozilla-thunderbird ~/.thunderbird
```
If anything goes wrong, copy ~/1.mozilla-thunderbird to ~/.thunderbird.

---

### Post by keheikev on 2010-07-01
> **FrancoNero said:**
> what's even more frustrating, is that one of the key addons for Thunderbird only works with 3.1 in its latest version

[http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html](http://www.mozilla.org/projects/calendar/releases/lightning1.0b2.html)

that makes an available upgrade to 3.1 ond Ubuntu even more essential. How hard is it to supply a .deb 64bit of this application? I just don't understand...
I am using 32 bit Ubuntu 9.04 and I am trying to install it using the instructions from [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) and here [http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla) and I did notice the keyserver was very slow I had to use the latters instructions from the web to download the pgp key but my software sources wont update as it need s gpg key? I did download the *.tar.bz2 file and tried this [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html) but that errored out on the decompressing the archive in my terminal.
:kihei

---

### Post by frwmbl on 2010-07-02
I run Ubuntu 9.04 (I have a new computer coming and won't go through the hassle of upgrading first to 9.10 and then to 10.04 on this old one!) and my issue was somewhat different: TB 3.1 started but with blank panes, except in safe mode. I disabled all extensions to no avail.  Eventually  I downgraded to 3.0.5 from [http://sourceforge.net/projects/ubuntuzilla/files/mozilla/](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/) and locked the version.  I wonder if Umang's fix will work for me?  I have a whole bunch of accounts for the whole family to back up so I'd appreciate to know first if anybody else had the same problem and the fix worked for them on 9.04.

(I should point out that although I'm a forum newbie I'm no Ubuntu newbie -- at least I've been on since 8.04 but have had no occasion to post to the forums before!)

---

### Post by nanotube on 2010-07-02
> **keheikev said:**
> I am using 32 bit Ubuntu 9.04 and I am trying to install it using the instructions from [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page) and here [http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla) and I did notice the keyserver was very slow I had to use the latters instructions from the web to download the pgp key but my software sources wont update as it need s gpg key? I did download the *.tar.bz2 file and tried this [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html) but that errored out on the decompressing the archive in my terminal.
:kihei

Hi
just tried the apt-key command and had no problems getting the key... maybe try again? maybe check if you have any outgoing firewall filtering?

---

### Post by nanotube on 2010-07-02
> **frwmbl said:**
>  I wonder if Umang's fix will work for me?  I have a whole bunch of accounts for the whole family to back up so I'd appreciate to know first if anybody else had the same problem and the fix worked for them on 9.04.


only way to know if it will work is to try it :)

---

### Post by nanotube on 2010-07-02
> **Umang said:**
> Hi all,

The issue, as discussed on the enigmail forums is because of some permissions issue cause by the ~/.thunderbird -> ~/.mozilla-thunderbird symlink. Running the following commands should help:

```
 $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
 $ unlink ~/.thunderbird
 $ mv ~/.mozilla-thunderbird ~/.thunderbird
```
If anything goes wrong, copy ~/1.mozilla-thunderbird to ~/.thunderbird.

looks like this is caused by a bug in firefox/thunderbird core... I tracked down the following:
[https://bugzilla.mozilla.org/show_bug.cgi?id=576233](https://bugzilla.mozilla.org/show_bug.cgi?id=576233)
[https://bugzilla.mozilla.org/show_bug.cgi?id=551152](https://bugzilla.mozilla.org/show_bug.cgi?id=551152)

So... until it is fixed, people with symlinks will have to de-symlink their profiles...

---

### Post by Norm24 on 2010-07-17
I really don't like 3.0.5.I've seen and used 3.1 on a Windows machine and absolutely find it to be major improvement.Having gone thru hell and back with 3.1 in Ubuntu I'm unwilling to try it again until this is fixed.

Any new news regarding this bug?

---

### Post by keheikev on 2010-07-17
Its been working fine for me for weeks now. You should probably use the installation instructions from the two above urls I supplied as all the messing with sym links makes me a little sick. Definitely backup your profiles.
:kihei

---

### Post by Umang on 2010-07-17
Yes. I've not had any problems after getting rid of the symlink.

---

### Post by Norm24 on 2010-07-18
How does one get rid of the symlink?What exactly should be done?

---

### Post by keheikev on 2010-07-18
I think Nanotubes explanation explains it. I have not had to unlink the links are you able to install tbird 3.1?
:kihei

---

### Post by Norm24 on 2010-07-18
I don't know what a symbolic link is.What folder is it in?What should I look for?Do I delete it?

---

### Post by Umang on 2010-07-18
> **Norm24 said:**
> How does one get rid of the symlink?What exactly should be done?
```

 $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
 $ unlink ~/.thunderbird
 $ mv ~/.mozilla-thunderbird ~/.thunderbird

```

---

### Post by Norm24 on 2010-07-19
> **Umang said:**
> ```

 $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
 $ unlink ~/.thunderbird
 $ mv ~/.mozilla-thunderbird ~/.thunderbird

```

Error message is the same for all three:

```
Command not found
```

---

### Post by Norm24 on 2010-07-19
Never mind I figured it out.

The freaking $ should not have been included at the beginning of each command line...#-o!

---

### Post by Umang on 2010-07-19
Yes, it's there to indicate that you have to enter it into a prompt. You'll find many people using that $ sign too when copy pasting terminal commands once you start using the terminal a lot.

To elaborate, it's used to distinguish terminal input from output. If you type "ps -e | grep bash" (without quotes) into the terminal, you'll want to see the output. Here's how you'd tell someone, I typed that and got this:
```
$ ps -e | grep bash
 2900 pts/0    00:00:01 bash
```

EDIT: You'll also see that you can do it for your reply also:

```
$  $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
bash: $: command not found
```

---

### Post by Norm24 on 2010-07-20
> **Umang said:**
> Yes, it's there to indicate that you have to enter it into a prompt. You'll find many people using that $ sign too when copy pasting terminal commands once you start using the terminal a lot.

To elaborate, it's used to distinguish terminal input from output. If you type "ps -e | grep bash" (without quotes) into the terminal, you'll want to see the output. Here's how you'd tell someone, I typed that and got this:
```
$ ps -e | grep bash
 2900 pts/0    00:00:01 bash
```

EDIT: You'll also see that you can do it for your reply also:

```
$  $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
bash: $: command not found
```

Once I figured out the $ doesn't belong I was all set.Anyways thanks for the help...back up and running where I want to be.

---

### Post by JuanT on 2010-07-23
> **nanotube said:**
> Hi,
Well, using the approach taken by ubuntuzilla, which is to pack the original mozilla build binaries into a .deb, it is approximately impossible - since mozilla doesn't make 64bit binary releases.

If you want 64bit, you can compile it from mozilla source yourself, or use the mozilla daily builds repo. 

thunderbird-stable repo still only has 3.0.5... so that one is a no-go for now.

If you are using Ubuntu 10.04 (including 64bit) you can get Thunderbird 3.1 from this repo: [http://ppa.launchpad.net/eugenesan/mozilla/ubuntu](http://ppa.launchpad.net/eugenesan/mozilla/ubuntu)
Just open a console and run the following commands:
Add the repo:
```
sudo add-apt-repository ppa:eugenesan/mozilla
```Refresh the package list and install the new thunderbird version
```
sudo apt-get update
sudo apt-get install thunderbird

```For those using Lightning in 64 bit:
When I tried to update the Lightning version to 1.0 I received an error saying that were not aviable in 64bit. I found here a 64 bit version [http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2rc3/contrib/linux-x86_64/) Just download the .xpi and intall it in Thunderbird via Tools>Add-ons>Install

---

### Post by jcoles on 2010-07-24
Thunderbird 3.1 is working well for me on 64-bit Lucid.

I installed Thunderbird 3.1 using the tar.bz2 file from Mozilla, not apt-get. It was quite simple:

[LIST=1]
[*]Copy the thunderbird tar.bz2 file to /usr/local.
[*]Extract the tar.bz2 file. This creates a new directory called thunderbird.
[*]In Preferred Applications, under Mail Reader, select Custom and set the command to /usr/local/thunderbird/thunderbird "%u". Make the same modification to the command in your task bar launcher if you have one.
[/LIST]

Obviously, root or sudo access is required to work in /usr/local. I made things a little easier for myself by starting a root window in nautilus, like this:

sudo nautilus --no-desktop /usr/local

From the nautilus window, I opened a second tab and found my download location, then copied the tar.bz2 file to /usr/local. I right-clicked the tar.bz2 file in /usr/local and selected Extract Here.

---

### Post by Umang on 2010-07-24
> **jcoles said:**
> Thunderbird 3.1 is working well for me on 64-bit Lucid.

I installed Thunderbird 3.1 using the tar.bz2 file from Mozilla, not apt-get. It was quite simple:

[LIST=1]
[*]Copy the thunderbird tar.bz2 file to /usr/local.
[*]Extract the tar.bz2 file. This creates a new directory called thunderbird.
[*]In Preferred Applications, under Mail Reader, select Custom and set the command to /usr/local/thunderbird/thunderbird "%u". Make the same modification to the command in your task bar launcher if you have one.
[/LIST]

Obviously, root or sudo access is required to work in /usr/local. I made things a little easier for myself by starting a root window in nautilus, like this:

sudo nautilus --no-desktop /usr/local

From the nautilus window, I opened a second tab and found my download location, then copied the tar.bz2 file to /usr/local. I right-clicked the tar.bz2 file in /usr/local and selected Extract Here.
That's more or less what Ubuntuzilla does.

---

### Post by nanotube on 2010-07-25
> **Umang said:**
> That's more or less what Ubuntuzilla does.

just not for 64bit systems ;)

---

### Post by Umang on 2010-07-25
When will I ever remember to remember that? :p

---

### Post by nanotube on 2010-07-25
> **Umang said:**
> When will I ever remember to remember that? :p

hehe hopefully mozilla will start releasing 64bit binaries soon, and then you won't have to anymore ;)

iirc, ff4 is supposed to be when they start making 64bit releases... we'll see...

---

### Post by abumaia on 2010-07-25
What is the function of the config setting mail.strict_threading when set to True?  Does it enable threading by subject line, or disable it?

I ask, because I have several emails not threading correctly: [http://www.4shared.com/photo/fOmeuJfW/Screenshot.html](http://www.4shared.com/photo/fOmeuJfW/Screenshot.html) , no matter what the config settings say.

---

### Post by nanotube on 2010-07-26
> **abumaia said:**
> What is the function of the config setting mail.strict_threading when set to True?  Does it enable threading by subject line, or disable it?

I ask, because I have several emails not threading correctly: [http://www.4shared.com/photo/fOmeuJfW/Screenshot.html](http://www.4shared.com/photo/fOmeuJfW/Screenshot.html) , no matter what the config settings say.

Hi,
a quick google reveals the following:
[https://wiki.mozilla.org/MailNews:Message_Threading#mail.strict_threading](https://wiki.mozilla.org/MailNews:Message_Threading#mail.strict_threading)

summary: if you want to thread by subject, set it to false.

---

### Post by abumaia on 2010-07-26
That was my initial interpretation of that page as well, however if you look at the other image I have up on that site with my screenshot, that is how I have TB set up, and yet I still get those replies as different threads than the original emails.  I've set those settings every which way I can think of, to no avail.  I don't know what's wrong with this thing.

---

### Post by nanotube on 2010-07-26
> **abumaia said:**
> That was my initial interpretation of that page as well, however if you look at the other image I have up on that site with my screenshot, that is how I have TB set up, and yet I still get those replies as different threads than the original emails.  I've set those settings every which way I can think of, to no avail.  I don't know what's wrong with this thing.

hmm... well, a better forum to ask your question would be on the mozilla forums (or the general support forum section here on ubuntuforums). i don't use threading in tb myself, so not familiar with the details...

---

### Post by shane2peru on 2010-07-27
> **jcoles said:**
> Thunderbird 3.1 is working well for me on 64-bit Lucid.

I installed Thunderbird 3.1 using the tar.bz2 file from Mozilla, not apt-get. It was quite simple:

[LIST=1]
[*]Copy the thunderbird tar.bz2 file to /usr/local.
[*]Extract the tar.bz2 file. This creates a new directory called thunderbird.
[*]In Preferred Applications, under Mail Reader, select Custom and set the command to /usr/local/thunderbird/thunderbird "%u". Make the same modification to the command in your task bar launcher if you have one.
[/LIST]

Obviously, root or sudo access is required to work in /usr/local. I made things a little easier for myself by starting a root window in nautilus, like this:

sudo nautilus --no-desktop /usr/local

From the nautilus window, I opened a second tab and found my download location, then copied the tar.bz2 file to /usr/local. I right-clicked the tar.bz2 file in /usr/local and selected Extract Here.

I installed this basically the same way, but I always put extra apps in /opt.  Works great for me.

Shane

---

### Post by wenfuli on 2010-07-28
I had Lightning running under Thunderbird before, but I had to do a complete re-install of ubuntu (long story, don't ask for now) and when I re-installed Thunderbird and tried to install Lightning, well...apparently the version of Lightning I got only works with TB 3.1 which is not officially available and the version I have -- after an update this morning -- is 3.06, and well, ....I'm sure you all know that or could at least guess.

I would love to get Lightning back on my system but do to that I need to install TB 3.1. So my question is: Is it safe to install it? I don't have the free time to go in and make countless back ups and then remove 3.1 and re-install 3.06 and set everything back up again.....Can I install 3.1 -- using the methods I've seen here -- on ubuntu 10.04 with no worries?

---

### Post by shane2peru on 2010-07-28
One extra step that I did was to zip/tar my .thunderbird directory.  This will only take about 5 min and is a step worth taking.  You can do this with GUI pretty easy.  

1.  Close Thunderbird Go to Places -> Home and then hit 'ctrl-h' which will show the hidden folders. Or View show hidden folders.  

2.  Then find the .thunderbird folder right click on the folder and select compress, pick a name and how you want it compressed, and wait for it to finish.  

**Note:**  If you don't remove the **.** in front of thunderbird, your backup will be a hidden file.  

**Note:**  If the .thunderbird file has a little arrow on the folder, then look for the .mozilla-thunderbird folder.  The little arrow means that it is a link (shortcut) and not the actual folder.  

Now TB is backed up, and you are ready to remove TB3.06 and install TB3.1 if anything goes wrong, reinstall 3.06 and remove the .thunderbird folder and unzip your backup to the original location.  

I installed TB3.1 yesterday, and seems to work fine.  I even took the liberty to install a few other extensions.  Seems to work like a charm.

Shane

---

### Post by wenfuli on 2010-07-28
Here's another question: Is everything automatically imported into 3.1? Assuming everything goes smoothly, will all my mails, accounts, and contacts be there waiting for me in 3.1 or will I have to import everything? I have some important mails for work in my local folders in TB 3.06 that I would not want to lose. I know I could back them up and import them, but as I said before, I am quite swamped with things to do and don't really have the time to sit here setting things up. I would only want to go to 3.1 if the upgrade were seamless. I don't need Lightning THAT badly.

---

### Post by shane2peru on 2010-07-28
> **wenfuli said:**
> Here's another question: Is everything automatically imported into 3.1? Assuming everything goes smoothly, will all my mails, accounts, and contacts be there waiting for me in 3.1 or will I have to import everything? I have some important mails for work in my local folders in TB 3.06 that I would not want to lose. I know I could back them up and import them, but as I said before, I am quite swamped with things to do and don't really have the time to sit here setting things up. I would only want to go to 3.1 if the upgrade were seamless. I don't need Lightning THAT badly.

I was using thunderbird before with the TB from the repos, and some update happened and broke thunderbird.  After a few weeks without it, I finally got around to upgrading.  When I upgraded everything imported fine, and worked.  The only problem that I have heard of is the extensions sometimes give you hassles.  In my case it told me what didn't work with 3.1 and looked for updates.  So yes it **should**  import everything fine.

Shane

PS - Do your backup in case it doesn't. :)

---

### Post by witeshark17 on 2010-07-28
Is there any update on having TB in the repos? Just curious as I'm rather happy enough with Evolution. :popcorn:

---

### Post by wenfuli on 2010-07-29
Just installed TB 3.1 as per JuanT's directions and everything seems to be working fine. I've got Lightning back now, and all my mail and settings imported fine. Looks good.

Now to see if I can get my calendars synced between my Mac and Linux machines. But that's probably a topic for another thread, if not another forum entirely.

Chuck

---

### Post by jxkauffold on 2010-07-29
> **Umang said:**
> Hi all,

The issue, as discussed on the enigmail forums is because of some permissions issue cause by the ~/.thunderbird -> ~/.mozilla-thunderbird symlink. Running the following commands should help:

```
 $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
 $ unlink ~/.thunderbird
 $ mv ~/.mozilla-thunderbird ~/.thunderbird
```If anything goes wrong, copy ~/1.mozilla-thunderbird to ~/.thunderbird.


The first command gives the response:

```
 $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
cp: omitting directory `~/.mozilla-thunderbird'
```

which is fixed by using cp -r but then the second command gives me this:

```
 $ unlink ~/.thunderbird
unlink: cannot unlink `~/.thunderbird': Is a directory
```

What am I missing?

---

### Post by nanotube on 2010-07-29
> **jxkauffold said:**
> The first command gives the response:

```
 $ cp ~/.mozilla-thunderbird ~/1.mozilla-thunderbird
cp: omitting directory `~/.mozilla-thunderbird'
```

which is fixed by using cp -r but then the second command gives me this:

```
 $ unlink ~/.thunderbird
unlink: cannot unlink `~/.thunderbird': Is a directory
```

What am I missing?

you're missing the fact that you don't need to do any of this if your .thunderbird is the actual directory with your mail, rather than a symlink to ~/.mozilla-thunderbird. :)

---

### Post by allanxyz on 2010-08-25
Mozilla has released the first Thunderbird 3.1 beta for Windows, Mac and Linux.
  Codenamed Lanikai, version 3.1 of Mozilla's open source email and  news client is built atop Gecko 1.9.2, the same rendering engine at the  heart of the new Firefox 3.6.  1.According to a Mozilla []("https://developer.mozilla.org/devnews/index.php/2010/03/10/lanikai-beta-1-preview-release-is-now-available-for-download/"),  the first "stable" Lanikai release includes several fixes to improve  upgrades from Thunderbird 2; several for auto complete, tabs and  activity manager, several design improvements and corrections to the  user interface, and various stability and memory improvements. A  complete list of bug fixes is available [http://www.elinkslondon.org/](http://www.elinkslondon.org/).
    [[IMG]http://ad.uk.doubleclick.net/ad/reg.software.4159/applications;tile=2;pos=top;dcove=d;sz=336x280;ord=THSvZsCoAT4AAH2bw78AAAOT?[/IMG]]("http://ad.uk.doubleclick.net/jump/reg.software.4159/applications;tile=2;pos=top;dcove=d;sz=336x280;ord=THSvZsCoAT4AAH2bw78AAAOT?")

---

