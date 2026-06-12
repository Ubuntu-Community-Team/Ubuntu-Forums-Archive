---
title: "HOWTO: Amend your hosts file to block ads (by site)"
date: 2006-08-22
forum: Tutorials
---

### Post by goldaryn on 2006-08-22
Note: this is very much a beginner's guide.


Q: What is a HOSTS file / Why might I want to do this?
A: It's explained nicely at [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)


Q: But why do this in Ubuntu? My Ubuntu is like a shield of steel!
A: Many reasons. But mainly to save bandwidth by not loading lots of rubbish. For each site listed as 127.0.0.1, content (usually ad banners etc) from that site isn't loaded. In a web browser that picture/frame will 404.

So, how to do it:
The host file in Linux lives at /etc/hosts. We are going to add some lines to it.

Disclaimer:

[SIZE="3"]******* NOW HEAR THIS *******[/SIZE]

[SIZE="3"]A) ***BACK UP*** your /etc/hosts BEFORE YOU START

B) You must APPEND to (not overwrite) the file. You need the stuff that's already in there! That means: paste in the additional lines AFTER what's already in there!

C) I do not recommend doing this if you HOST WEB PAGES from your PC.
[/SIZE]

End of disclaimer.



1) >>>>>>> BACKUP YOUR HOSTS FILE <<<<<<<<<

$ sudo cp /etc/hosts /etc/hosts.old

2) Download a good hosts file. I recommend the MVPs one: 

[http://www.mvps.org/winhelp2002/hosts.txt](http://www.mvps.org/winhelp2002/hosts.txt)

3) Open your hosts file.

$ sudo gedit /etc/hosts

4) Paste in the contents of hosts.txt into the bottom of /etc/hosts.

5) It should take effect immediately. Close and reload your web browser then try to go to one of the blocked sites. It should 404.

Luc

---

### Post by bodhi.zazen on 2006-09-16
Here is a link to a site with a script to update your hosts file:

[hostsfile.mine](http://hostsfile.mine.nu/downloads/)

Look on the **very bottom** of the page for this:

[color=red]Unix/Linux bash Hosts updater script (txt)  (m)[/color]

Here is the script if you would like to examine the code:

[Hosts update script](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)

[list][*]Download the script
[*]Make the script executable (chmod a+x updatehosts.sh)
[*]Install tofrodos (sudo apt-get install tofrodos)
[*] sudo ./updatehosts.sh[/list]

[color=blue]Optional[/color] 
127.0.0.1 = your computer
0.0.0.0 = nowhere

"0.0.0.0" is faster as "127.0.0.1" will wait for a timeout :twisted: 


This command will change 127.0.0.1 to 0.0.0.0 :
```
sudo sed -i -e 's_127.0.0.1_0.0.0.0_g' /etc/hosts
```

[color=red]WARNING: We now need to manually edit /etc/hosts and change the line(s) at the top with localhost and your hostname back to 127.0.0.1 localhost[/color]

> #These may be on one line or multiple lines
127.0.0.1       localhost
127.0.0.1       Ubuntu  # Change Ubuntu to your hostname

It is best to do this from the terminal with vim or nano as graphical editors will take forever to load (the hosts file is large).

---

### Post by angler on 2006-10-16
After running the script, which ran seemlessly, I don't see any changes to the HOSTS file... which one should it change? I was hoping to do like I did in windoze and cut/paste the loopbacks into the file, but I lost admin rights when I did it. Maybe I made a n00b mistake, I'll try it again. thanks

---

### Post by bodhi.zazen on 2006-10-16
it modifies /etc/hosts

If you lost admin rights, boot to failsafe.

If you do not know, to get your host name, at the CLI type:```
hostname
```

```
nano /etc/hosts
```Add the line> 127.0.0.1 localhost.localdomain <hostname>
<hostname> = your host nameAt the top fo the file.

Crtl-X to exit, type Y to save.

Reboot```
reboot
```

---

### Post by 666porcondissaum on 2008-11-17
Thank you very much.:confused:

---

### Post by Mark_in_Hollywood on 2010-02-11
Following this post, I read:

Unix/Linux bash Hosts updater script (txt) (m)

Here is the script if you would like to examine the code:

Hosts update script

    * Download the script
    * Make the script executable (chmod a+x updatehosts.sh)
    * Install tofrodos (sudo apt-get install tofrodos)
    * sudo ./updatehosts.sh


I downloaded the updatehosts.sh.txt

but, doing: chmod a+x updatehosts.sh -- did not remove the .txt. So there I quit and am asking for clarification:

Do I rename the file updatehosts.sh.txt manually before or after running chomd a+x?

---

### Post by bodhi.zazen on 2010-02-12
> **Mark_in_Hollywood said:**
> Do I rename the file updatehosts.sh.txt manually before or after running chomd a+x?

It does not matter if you rename the file before or after the chomd.

---

### Post by mr.nope on 2010-04-21
On Ubuntu Lucid Lynx 10.04 the script is currently broken because of the following changes to the tofrodos package.

[QUOTE="/usr/share/doc/tofrodos/NEWS.Debian.gz"]

tofrodos (1.7.8.debian.1-2) unstable; urgency=low

  With this release the symlinks "unix2dos" and "dos2unix" are dropped from the
  package.  This will allow the introduction of the original dos2unix package,
  which also supports conversion to MacOS style files.

  Should you have scripts depending on these symlinks, I recommend using
  shell-aliases, like in the following example for bash:

   alias unix2dos="/usr/bin/fromdos -u"  (or todos)
   alias dos2unix="/usr/bin/fromdos -d"  (or just fromdos)

 -- Alexander Reichle-Schmehl <tolimar@debian.org>  Thu, 21 Jan 2010 20:59:11 +0100[/QUOTE]

I simply updated the script by replacing all occurrences of [FONT="Courier New"]dos2unix[/FONT] with [FONT="Courier New"]fromdos[/FONT] using gedit (CTRL+H). Works like a charm now.

---

### Post by Helkaluin on 2010-05-30
Just want to put a reminder here for all who are looking into using /etc/hosts to block ads: this seem to break desktopcouch, and with that UbuntuOne and Gwibber and Evolution. Multiple beam.smp processes will be spawned, sucking up CPU cycles, and seem to take forever to parse lines in /etc/hosts

The bug is here: [https://bugs.launchpad.net/ubuntu/lucid/+source/desktopcouch/+bug/530541](https://bugs.launchpad.net/ubuntu/lucid/+source/desktopcouch/+bug/530541)

Chad on the page suggested dnsmasq or similar as an alternative to /etc/hosts for the time being...

---

### Post by SonicsDemon on 2010-05-30
Awesome! \\:D/ I love this script! Thanks!

---

### Post by ipernar on 2010-06-09
> **bodhi.zazen said:**
> Here is a link to a site with a script to update your hosts file:

[hostsfile.mine](http://hostsfile.mine.nu/downloads/)



here is my host file if you wish to block porn :)

[http://datasaver.orgfree.com/hosts.zip](http://datasaver.orgfree.com/hosts.zip)
xthosts no longer works so I had 2 change! :)

---

### Post by bodhi.zazen on 2010-06-09
> **ipernar said:**
> here is my host file if you wish to block porn :)

[http://user.xthost.info/zelenalista/hosts.zip](http://user.xthost.info/zelenalista/hosts.zip)

thank you !!

The zip file does not download =(

---

### Post by ipernar on 2010-06-10
> **bodhi.zazen said:**
> thank you !!

The zip file does not download =(

Dude it must download :)
just click download (2times) after clicking the link

One friend of mine was at my apartment (slept over) and he wanted to search for porn on my comp and was shocked to realise he cant get it... hahah

It was funny to see his face, i said... wazap bro... no porn today... and he said... yeah dude, i searched...but couldnt get into site...

email me if yoou want me to send it via email ;)
[email]ipernar@yahoo.com[/email]

---

### Post by TheTank on 2010-06-10
> **bodhi.zazen said:**
> 
[color=blue]Optional[/color]
127.0.0.1 = your computer
0.0.0.0 = nowhere

"0.0.0.0" is faster as "127.0.0.1" will wait for a timeout :twisted: 


This command will change 127.0.0.1 to 0.0.0.0 :
```
sudo sed -i -e 's_127.0.0.1_0.0.0.0_g' /etc/hosts
```

[color=red]WARNING: We now need to manually edit /etc/hosts and change the line(s) at the top with localhost and your hostname back to 127.0.0.1 localhost[/color]

1st off, great suggestion! Thanks

2nd I would not do it this way.
What I would do is apply the 127.0.0.1 -> 0.0.0.0 on the mvp file.

Workflow:
download mvp file
apply the mentioned sed to it
then take a hosts.base and concat the mvp file to it and write it out to /etc/hosts

---

### Post by bodhi.zazen on 2010-06-10
> **ipernar said:**
> Dude it must download :)
just click download (2times) after clicking the link

One friend of mine was at my apartment (slept over) and he wanted to search for porn on my comp and was shocked to realise he cant get it... hahah

It was funny to see his face, i said... wazap bro... no porn today... and he said... yeah dude, i searched...but couldnt get into site...

email me if yoou want me to send it via email ;)
[EMAIL="ipernar@yahoo.com"]ipernar@yahoo.com[/EMAIL]

Had to allow cookies to DL the zip file.

OMG that is one huge hosts file, lol

---

### Post by daggoth8 on 2010-08-29
Looking at the hosts updatehosts.sh script from

    [http://hostsfile.mine.nu/downloads/updatehosts.sh.txt](http://hostsfile.mine.nu/downloads/updatehosts.sh.txt)

There could be a possible bug with the sanity test on line 54. 

    if [ 'grep -c "banner" /tmp/hosts' ];then 

Did the author accidently put quotes around the grep, instead of using
backticks? Perhaps it could have been written like this instead...

    if [ $( grep -c "banner" /tmp/hosts ) ] ; then
  
That said, the script works perfectly, so thanks :-)





[]("http://hostsfile.mine.nu/downloads/updatehosts.sh.txt")

---

### Post by rocksockdoc on 2010-10-02
There is an unmentioned "problem" here, in practical terms, which can be rectified easily, if you know how.

The problem is how to merge multiple huge hosts files and to rid yourself of duplicate entries.

Just one solution is to use the following command post merger is to employ "sort -u".
 $ sudo sort -u /etc/hosts -o /etc/hosts

Since you probably don't want the first few lines sorted, do a 'mark a'
ma

And then, just because, do a mark b:
mb

And then run the command:
:'a,'b!sort -u

Which is, "from a, to b, sort -unique".

---

### Post by BTA on 2011-03-14
Hi, I'm a first time Ubuntu user (aka Super Beginner) - This is my first post and I realize this is an old thread but I needed some help with the script updating my host file:

I installed tofrodos and when I do the last step - "sudo ./updatehosts.sh" - I get this message: 

-------------------------------------------------------------
This script will update your Hosts file to the latest version
Your original Hosts file will be renamed to /etc/hosts.original
-------------------------------------------------------------

Checking for required applications...
... wget
... unzip
... dos2unix
tofrodos (which contains dos2unix) is missing.
... grep
One or more required applications are missing. Aborting now ...
adam@adam-MT6840:~$ 

It says I'm missing tofrodos which contains dos2unix.  I've scoured the internet and these forums but I cannot find a solution.  Any suggestions??

Thanks

---

### Post by bodhi.zazen on 2011-03-14
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tofromdos&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tofromdos&searchon=name&subword=1&version=all&release=all)

sudo apt-get install tofromdos

---

### Post by DGINSD on 2011-04-05
> **bodhi.zazen said:**
> [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tofromdos&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tofromdos&searchon=name&subword=1&version=all&release=all)

sudo apt-get install tofromdos

I need help with using the update script, I'm very new with Ubuntu so I could use a little more detailed instruction on the process.  keeps getting killed saying I dont have tofrodos.

---

### Post by bodhi.zazen on 2011-04-05
> **DGINSD said:**
> I need help with using the update script, I'm very new with Ubuntu so I could use a little more detailed instruction on the process.  keeps getting killed saying I dont have tofrodos.

Read the post right above yours =)

---

### Post by DGINSD on 2011-04-05
> **bodhi.zazen said:**
> Read the post right above yours =)

I tried that it didn't work. Tried it again and loaded dostounix (I think it was)  as well and got it to work, but I have a few other questions as well.

How often should this script be run to update the hosts (weekly, monthly) or is it a one time deal?
 
Theres some conflicting posts in this thread about changing the host address to 0.0.0.0 instead of leaving them as 127.0.0.1 (or what ever standard is), some clairification on this?  Safe to do? Evolution and other mail programs still work?

Any other reccomended hosts lists to add?

Thank you for your help and  the info.

---

### Post by bodhi.zazen on 2011-04-05
OK, glad you got it working.

It is the same list as is used for AdblockPlus.

Update, up to you. I think the list itself is updated either daily or almost daily. I personally update it (when I use a hosts file) every few months, sooner if I start seeing ads.

On a desktop you could use either 0.0.0.0 or 127.0.0.1 , on a server (which I would not advise) you should probably use 127.0.0.1.

You can use either, easy enough to switch if you have a problem.

Alternates to a host file would include a proxy (privoxy) or using adblock extensions with your browser.

---

### Post by DGINSD on 2011-04-05
> **bodhi.zazen said:**
> OK, glad you got it working.

It is the same list as is used for AdblockPlus.

Update, up to you. I think the list itself is updated either daily or almost daily. I personally update it (when I use a hosts file) every few months, sooner if I start seeing ads.

On a desktop you could use either 0.0.0.0 or 127.0.0.1 , on a server (which I would not advise) you should probably use 127.0.0.1.

You can use either, easy enough to switch if you have a problem.

Alternates to a host file would include a proxy (privoxy) or using adblock extensions with your browser.

You say "when u use a hosts file" why would you ever need to do that, and how would you do that?  Isn't the bennifit of using 0.0.0.0 faster site loading. Some recomended reading on using a proxy (its a totally new idea to me so I know nothing about it). I think what I meant by alternatives is additions to the host file  such as know hijack sites and what not.

---

### Post by DGINSD on 2011-04-06
> **DGINSD said:**
> You say "when u use a hosts file" why would you ever need to do that, and how would you do that?  Isn't the bennifit of using 0.0.0.0 faster site loading. Some recomended reading on using a proxy (its a totally new idea to me so I know nothing about it). I think what I meant by alternatives is additions to the host file  such as know hijack sites and what not.

Just realized I didn't phrase my first question correctly, what I meant was why would you ever not want to use a hosts file? What need would there be to do that?

---

### Post by bodhi.zazen on 2011-04-06
> **DGINSD said:**
> Just realized I didn't phrase my first question correctly, what I meant was why would you ever not want to use a hosts file? What need would there be to do that?

A hosts file is one option, other options include using a proxy (priviox / squid) and a third is extensions on browsers.

Each has advantages and disadvantages.

The disadvantage of a hosts file is that you need to manually keep the list up to date and you would have to keep it up to date on each desktop.

The disadvantage of browser extensions is that they apply to a single browser for a single user. The advantage is that these lists are typically more up to date and easier to customize per user.

For multiple users on a lan a proxy makes more sense, but it takes a bit more knowledge to set up and not all users may need the same content filtering.

You will have to decide for yourself what makes the most sense.
The

---

### Post by IT2870 on 2011-04-06
I had to log in just to thank you for this. I work in IT and never even knew about this.(never got deep into the internet\web part of IT)....What's got me so happy is I often work off of a broadband card when I'm out and about. I hate the freezing,especially any video(youtube,etc.) but just accepted it....until today. It's like i just went from a modem 54k to a DSL connection. THANK YOU!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by DGINSD on 2011-04-23
> **rocksockdoc said:**
> There is an unmentioned "problem" here, in practical terms, which can be rectified easily, if you know how.

The problem is how to merge multiple huge hosts files and to rid yourself of duplicate entries.

Just one solution is to use the following command post merger is to employ "sort -u".
 $ sudo sort -u /etc/hosts -o /etc/hosts

Since you probably don't want the first few lines sorted, do a 'mark a'
ma

And then, just because, do a mark b:
mb

And then run the command:
:'a,'b!sort -u

Which is, "from a, to b, sort -unique".

I need some help with this post I'm still finding my way around the terminal. The part I'm having trouble with is the mark A and mark B. How is this done, to mark certain lines, if possible a more detailed step by step? What directory, proper syntax to mark, or is that something that needs to be done with a text editor (the marking) to the hosts file it's self?

---

### Post by rocksockdoc on 2011-04-24
> **DGINSD said:**
> The part I'm having trouble with is the mark A and mark B. How is this done, to mark certain lines, if possible a more detailed step by step? 

I'll try to explain this but explaining 'vi' commands is, shall we say, a bit problematic, mainly because there are two modes and the commands only work in one of the two modes but there is no visual clue what mode you're in. Also, most of us have 'finger memory' ... which means the commands are embedded in our finger muscles - so - actually 'explaining' the steps is problematic. Those of you who know vi well know what I mean by that; if you don't know vi well, you won't really understand why that is the case. You'll learn.

Lastly, it takes VASTLY more time to explain than the two or three keystrokes take to do ... so it' 'seems' confusing ... but it's really simple. 

First off, once in vi, you MUST clearly get yourself in the command mode by using the ESCAPE key religiously! (Hit it once, hit it twice, and, for good effect, if you're uncertain, hit it thrice!). :) You only need to hit it once, but, I need to underscore the point that you must be in the right mode.

Also, you must be using a vi editor. There are lots of them. Vi, vim, Gvim, etc. (all will have 'vi' in the name somewhere). Or, just open up a terminal window and type:

```
vi /tmp/foo
```Once you have an empty file "foo" open, import the hosts file:
```
ESCAPE:r/etc/hosts
```The ":r" means to "read in" the file which follows "/etc/hosts".

Now, with your "j" key, move down (use the "k" key to move up). 

At some point, hit "mx" (that will mark that spot as an "x"). Then use your "j" and "k" key again to go to a different spot and then hit "my". Now you've marked a spot as a 'y').

At this point, do whatever you want between those two spots, e.g., to sort:
:'x,'y!sort

Which, interpreted, is:
: = command
'x = from x
'y = to y
!sort = run the sort command

If things don't seem to work, hit the escape key a few times (and stay away from the 'i' key while doing commands.

Hope this helps.
Rock

---

### Post by DGINSD on 2011-04-26
Firstly Thank you for the help, slowly but surely I'm learning

I got it to work but a few more details I'd like. What is vi I guess I mean in contrast to an editor like gedit?

When I do a "mx" should a physical mark be made on the document (e.g. an x) something to note you did it?

Are there any other navigation keys other than j and k, as that could take a very long time to get to the bottlom of a large hosts file? 

Save and exit, how do I do it?

I think thats it for now, again thank you for the help.

---

### Post by sdemsc on 2011-04-26
thanks. i am using script and works perfactly

---

### Post by DGINSD on 2011-05-03
Uh, so just a heads up. I was trying to  watch some flash videos on a web site, but for what ever reason the videos wouldn't play.  After an hour or two of trying to figure out what the hell was wrong, out of desperation I put my hosts file back to normal, and come to find out the site had placed ad's in the beginning of the video feeds which the hosts file in turn was blocking.

I was really enjoying the no ad's too. :(

Did I have something set up wrong, or is there a work around for this?

---

### Post by bodhi.zazen on 2011-05-04
> **DGINSD said:**
> Uh, so just a heads up. I was trying to  watch some flash videos on a web site, but for what ever reason the videos wouldn't play.  After an hour or two of trying to figure out what the hell was wrong, out of desperation I put my hosts file back to normal, and come to find out the site had placed ad's in the beginning of the video feeds which the hosts file in turn was blocking.

I was really enjoying the no ad's too. :(

Did I have something set up wrong, or is there a work around for this?

You can remove or comment out the offending host.

---

### Post by DGINSD on 2011-05-04
> **bodhi.zazen said:**
> You can remove or comment out the offending host.

How could I find out which one is causing the problem? The ad displayed was an AT&T ad, I inspected the element but was not smart enough to figure out where the ad was coming from.

My concern is more and more sites will follow this model to counter ad block methods. The sites I was using to test Chargers.com and NFL.com and both had ads  while the video loaded?  Oddly enough once in a while the video would play but it was rather irregular.

---

### Post by bodhi.zazen on 2011-05-04
> **DGINSD said:**
> How could I find out which one is causing the problem? The ad displayed was an AT&T ad, I inspected the element but was not smart enough to figure out where the ad was coming from.

My concern is more and more sites will follow this model to counter ad block methods. The sites I was using to test Chargers.com and NFL.com and both had ads  while the video loaded?  Oddly enough once in a while the video would play but it was rather irregular.

Well if that is the case, you might prefer NoScript , Adblock Plus, and Request Policy (addons).

If you inspect the elements, you will see (hopefully) "http://server.com"

search your hosts file for "server.com"

---

### Post by DGINSD on 2011-05-06
Will those addins work in any browser, I use Chromium as my default instead of Firefox. If so how do I go about getting them?

---

### Post by bodhi.zazen on 2011-05-06
> **DGINSD said:**
> Will those addins work in any browser, I use Chromium as my default instead of Firefox. If so how do I go about getting them?

Some of those addins are available for chormium yes, some not.

You will need to learn to manage your hosts file , that is the downside of this technique.

Open the file in gedit and search or use tools such as grep , sed, awk to automate the process.

---

### Post by mellowchuck123 on 2011-07-07
[B]Here's a hosts file I'd like to contribute to every one.

It's a combination of 12 up-to-date(as of this moment) lists that block ads and sites with malwares(viruses, trojans, worms etc.)

MAKE SURE YOU COPY THE ENTIRE FILE TO etc/hosts using root or sudo.

_DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-

127.0.0.1	localhost
127.0.1.1	YOUR HOST NAME GOES HERE


If you already have blocking entries, add this list to the bottom of your hosts file.[/B]


[http://ubuntuone.com/p/13J6/]("http://ubuntuone.com/p/13J6/")

-Chuck

---

### Post by mellowchuck123 on 2011-09-16
[CENTER]_[SIZE=4]**September 16, 2011 HOSTS file.**[/SIZE]_

[/CENTER]
[B] 
This is a combination of 12 up-to-date(as of this moment) lists that block  ads and sites with malwares(viruses, trojans, worms etc.)

MAKE SURE YOU COPY THE ENTIRE FILE TO etc/hosts using root or sudo.

_DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-

127.0.0.1	localhost
127.0.1.1	YOUR HOST NAME GOES HERE


If you already have blocking entries, add this list to the bottom of your hosts file.[/B]

[U][I][B]September 16th, 2011 HOSTS file link:

[/B][/I][/U][https://ubuntuone.com/6MVhZn91mwKeIvUoJl0CbK](https://ubuntuone.com/6MVhZn91mwKeIvUoJl0CbK)

---

### Post by mellowchuck123 on 2011-11-04
[CENTER]_[SIZE=4]**November 4, 2011 HOSTS file.**[/SIZE]_

[/CENTER]
[B] 
This is a combination of 12 up-to-date(as of this moment) lists that  block  ads and sites with malwares(viruses, trojans, worms etc.)

The file is optimized, sorted & is in 0.0.0.0 format.

MAKE SURE YOU COPY THE ENTIRE FILE TO /etc/hosts using root or sudo.

_DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-

127.0.0.1	localhost
127.0.1.1	YOUR HOST NAME GOES HERE


If you already have blocking entries, add this list to the bottom of your hosts file.[/B]

[U][I][B]November 4, 2011 HOSTS file link:

[http://ubuntuone.com/4o5KKT545F9M4WZUpKO7PB](http://ubuntuone.com/4o5KKT545F9M4WZUpKO7PB)



[/B][/I][/U]Side note- You might want to install an ad-blocking extension in your browser so you don't see the annoying "page not found" error where ads were before.

---

### Post by joneberger on 2011-11-17
> **mellowchuck123 said:**
> [CENTER]_[SIZE=4]**November 4, 2011 HOSTS file.**[/SIZE]_

[/CENTER]
[B] 
This is a combination of 12 up-to-date(as of this moment) lists that  block  ads and sites with malwares(viruses, trojans, worms etc.)

The file is optimized, sorted & is in 0.0.0.0 format.

MAKE SURE YOU COPY THE ENTIRE FILE TO /etc/hosts using root or sudo.

_DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-

127.0.0.1	localhost
127.0.1.1	YOUR HOST NAME GOES HERE


If you already have blocking entries, add this list to the bottom of your hosts file.[/B]

[U][I][B]November 4, 2011 HOSTS file link:

[http://ubuntuone.com/4o5KKT545F9M4WZUpKO7PB](http://ubuntuone.com/4o5KKT545F9M4WZUpKO7PB)



[/B][/I][/U]Side note- You might want to install an ad-blocking extension in your browser so you don't see the annoying "page not found" error where ads were before.

Awesome.  Perfect.

---

### Post by Aberdeen on 2011-11-17
Nice work and very much appreciated.;)

---

### Post by TheTank on 2011-11-21
> **mellowchuck123 said:**
> snip
Thanks for the continuous updates!

Quick question: have you checked the sites listed?
f.i. hidemyass.com is blocked, yet I was unaware that this is a problematic site.

I guess part of the list is also from a 'not desireable' list, perhaps used in companies. So it might be something to provide multiple such lists we can paste together to fit our needs.

thanks

---

### Post by mellowchuck123 on 2011-11-21
> **TheTank said:**
> Thanks for the continuous updates!

Quick question: have you checked the sites listed?
f.i. hidemyass.com is blocked, yet I was unaware that this is a problematic site.

I guess part of the list is also from a 'not desireable' list, perhaps used in companies. So it might be something to provide multiple such lists we can paste together to fit our needs.

thanks

All lists used are malwares and ads blocking hosts files. Sometimes these list maintainers make mistakes.

I can only check the sites I frequent. For instance- I use meebo.com and found that for whatever reason it was added to one of the lists I use to make this hosts file; it is now not blacklisted and I am in process of uploading hosts file for today. Therefore, if you find a entry that you believe shouldn't be in this list, I will gladly take it out if you give me a valid reason. I don't know what hidemyass.com is, but I'm assuming it's a proxy service; have you tried Tor? Do you like Tor if so? If you don't like Tor and prefer this site, why is this so?


-Chuck

---

### Post by mellowchuck123 on 2011-11-21
[CENTER]_[SIZE=4]**November 21, 2011 HOSTS file.**[/SIZE]_

[/CENTER]
[B] 
This is a combination of 9 up-to-date(as of this moment) lists that   block  ads and sites with malwares(viruses, trojans, worms etc.)

The file is optimized, sorted & is in 0.0.0.0 format.

MAKE SURE YOU COPY THE ENTIRE FILE TO /etc/hosts using root or sudo.

_DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-

127.0.0.1    localhost
127.0.1.1    YOUR HOST NAME GOES HERE


If you already have blocking entries, add this list to the bottom of your hosts file.[/B]

[U][I][B]November 21, 2011 HOSTS file link:

[http://ubuntuone.com/7333ex5gkroKUXKG44bfS7](http://ubuntuone.com/7333ex5gkroKUXKG44bfS7)



[/B][/I][/U]Side note- You might want to install an ad-blocking  extension in your browser so you don't see the annoying "page not found"  error where ads were before.

---

### Post by jmate24 on 2011-11-22
well the host file blocked my favorite flash video sites and all i really want is to block porn and also to make sure that the host file cannot be changed by any site but my own computer so i just copy and pasted the porn host file to my curent host file (of course after i made a backup of my original ```
sudo cp /etc/hosts /etc/hosts.old
```)

then i simply chmod-ed my host file to take away the write attribute.

```
sudo chmod a-w /etc/hosts
```

these lines are a good idea if you go to sites that try to hack/hijack your host file and make it point to their domain only.
by having a copy of your original and then making the host file ro then you can control what sites can be accessed from your computer (i.e. facebook, google, bing, hulu, etc.)

---

### Post by mellowchuck123 on 2011-11-22
> **jmate24 said:**
> well the host file blocked my favorite flash video sites and all i really want is to block porn and also to make sure that the host file cannot be changed by any site but my own computer so i just copy and pasted the porn host file to my curent host file (of course after i made a backup of my original ```
sudo cp /etc/hosts /etc/hosts.old
```)

then i simply chmod-ed my host file to take away the write attribute.

```
sudo chmod a-w /etc/hosts
```these lines are a good idea if you go to sites that try to hack/hijack your host file and make it point to their domain only.
by having a copy of your original and then making the host file ro then you can control what sites can be accessed from your computer (i.e. facebook, google, bing, hulu, etc.)

Which flash sites are blocked in the HOSTS file posted yesterday?

---

### Post by mellowchuck123 on 2011-11-22
Here are the 9 lists I currently use if you would like to use your own script instead and sort and update your own HOSTS file --

```
http://www.mvps.org/winhelp2002/hosts.zip

http://hphosts.gt500.org/hosts.zip

http://updates.it-mate.co.uk/updates.asp

http://hosts-file.net/ad_servers.asp

http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts&showintro=1&mimetype=plaintext

http://someonewhocares.org/hosts/hosts

http://support.it-mate.co.uk/downloads/HOSTS.txt

http://hostsfile.mine.nu/Hosts

http://www.securemecca.com/Downloads/hosts.txt
```

---

### Post by TheTank on 2011-11-23
> **mellowchuck123 said:**
> All lists used are malwares and ads blocking hosts files. Sometimes these list maintainers make mistakes.

I can only check the sites I frequent. For instance- I use meebo.com and found that for whatever reason it was added to one of the lists I use to make this hosts file; it is now not blacklisted and I am in process of uploading hosts file for today. Therefore, if you find a entry that you believe shouldn't be in this list, I will gladly take it out if you give me a valid reason. I don't know what hidemyass.com is, but I'm assuming it's a proxy service; have you tried Tor? Do you like Tor if so? If you don't like Tor and prefer this site, why is this so?
-Chuck
Thanks for the reply!

@hidemyass:
yes, it is simply a web proxy and I sometimes use it to a) check if there is something blocking my access to a site (censor) or if it is really down and b) do the same with content, f.i. when youtube blocks content because I live in the wrong country.

Plus such a censor tool need not only be national but also company thing.
Hence why I thought it might be a 'company block list' that filters out sites you can use to avoid sites blocked by companies.
Which in some cases is fine.

@Update:
Ok, will do. Thanks!

---

### Post by mellowchuck123 on 2011-11-23
> **TheTank said:**
> Thanks for the reply!

@hidemyass:
yes, it is simply a web proxy and I sometimes use it to a) check if there is something blocking my access to a site (censor) or if it is really down and b) do the same with content, f.i. when youtube blocks content because I live in the wrong country.

Plus such a censor tool need not only be national but also company thing.
Hence why I thought it might be a 'company block list' that filters out sites you can use to avoid sites blocked by companies.
Which in some cases is fine.

@Update:
Ok, will do. Thanks!

I willl remove hidemyass.com from my next update :) ;)

-Chuck

---

### Post by mellowchuck123 on 2011-12-03
[CENTER]_[SIZE=4]**December 3, 2011 HOSTS file.**[/SIZE]_



** This is a combination of 9 up-to-date(as of this moment) lists that    block  ads and sites with malwares(viruses, trojans, worms etc.)**

**LISTS USED -**
```
http://www.mvps.org/winhelp2002/hosts.zip

http://hphosts.gt500.org/hosts.zip

http://updates.it-mate.co.uk/updates.asp

http://hosts-file.net/ad_servers.asp

http://pgl.yoyo.org/as/serverlist.php?

hostformat=hosts&showintro=1&mimetype=plaintext

http://someonewhocares.org/hosts/hosts

http://support.it-mate.co.uk/downloads/HOSTS.txt

http://hostsfile.mine.nu/Hosts

http://www.securemecca.com/Downloads/hosts.txt

```**The file is optimized, sorted & is in 0.0.0.0 format.**

** MAKE SURE YOU COPY THE ENTIRE FILE TO /etc/hosts using root or sudo.**

** _DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-**

** 127.0.0.1    localhost**
** 127.0.1.1    YOUR HOST NAME GOES HERE**


** If you already have blocking entries, add this list to the bottom of your hosts file.**

_***December 3, 2011 HOSTS file link:***_
[SIZE=4]
_*** [http://ubuntuone.com/6bcMKbj5S6cs8BUDe0rFSr](http://ubuntuone.com/6bcMKbj5S6cs8BUDe0rFSr)***_[/SIZE] 


Side note- You might want to install an ad-blocking   extension in your browser so you don't see the annoying "page not found"   error where ads were before.[/CENTER]

---

### Post by mellowchuck123 on 2011-12-18
[CENTER]_[SIZE=4]**December 18, 2011 HOSTS file.**[/SIZE]_



** This is a combination of 9 up-to-date(as of this moment) lists that     block  ads and sites with malwares(viruses, trojans, worms etc.)**

**LISTS USED -**
[/CENTER]
       [CENTER]    ```
http://www.mvps.org/winhelp2002/hosts.zip

http://hphosts.gt500.org/hosts.zip

http://updates.it-mate.co.uk/updates.asp

http://hosts-file.net/ad_servers.asp

http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts&showintro=1&mimetype=plaintext

http://someonewhocares.org/hosts/hosts

http://support.it-mate.co.uk/downloads/HOSTS.txt

http://hostsfile.mine.nu/Hosts

http://www.securemecca.com/Downloads/hosts.txt
```
**The file is optimized, sorted & is in 0.0.0.0 format.**

** MAKE SURE YOU COPY THE ENTIRE FILE TO /etc/hosts using root or sudo.**

** _DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-**

** 127.0.0.1    localhost**
** 127.0.1.1    YOUR HOST NAME GOES HERE**


** If you already have blocking entries, add this list to the bottom of your hosts file.**

_***December 18, 2011 HOSTS file link:***_

[SIZE=4] _*** []("http://ubuntuone.com/6bcMKbj5S6cs8BUDe0rFSr")***_[/SIZE][[SIZE=4] _*** http://ubuntuone.com/0Z6rhNrarrmehKCRcaLMh6***_[/SIZE]]("http://ubuntuone.com/0Z6rhNrarrmehKCRcaLMh6")


Side note- You might want to install an ad-blocking   extension in your  browser so you don't see the annoying "page not found"   error where ads  were before.[/CENTER]

---

### Post by mellowchuck123 on 2011-12-29
[CENTER]_[SIZE=4]**December 29, 2011 HOSTS file.**[/SIZE]_



** This is a combination of 9 up-to-date(as of this moment) lists that      block  ads and sites with malwares(viruses, trojans, worms etc.)**

**LISTS USED -**
```
http://www.mvps.org/winhelp2002/hosts.zip

http://hphosts.gt500.org/hosts.zip

http://updates.it-mate.co.uk/updates.asp

http://hosts-file.net/ad_servers.asp

http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts&showintro=1&mimetype=plaintext

http://someonewhocares.org/hosts/hosts

http://support.it-mate.co.uk/downloads/HOSTS.txt

http://hostsfile.mine.nu/Hosts

http://www.securemecca.com/Downloads/hosts.txt
```

 **The file is optimized, sorted & is in 0.0.0.0 format.**

** MAKE SURE YOU COPY THE ENTIRE FILE TO /etc/hosts using root or sudo.**

** _DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-**

** 127.0.0.1    localhost**
** 127.0.1.1    YOUR HOST NAME GOES HERE**


** If you already have blocking entries, add this list to the bottom of your hosts file.**

_***December 29, 2011 HOSTS file link:***_

**[SIZE=4][http://ubuntuone.com/7QOZkqtE8Tn6Mp77pvePQG](http://ubuntuone.com/7QOZkqtE8Tn6Mp77pvePQG)[/SIZE]**


Side note- You might want to install an ad-blocking   extension in your   browser so you don't see the annoying "page not found"   error where  ads  were before.[/CENTER]

---

### Post by bzd454 on 2011-12-29
thanks mellowchuck...

dumb question, i was wondering if there is a way to alphabetize it?  because it blocks file hosting sites and a few others that i'd rather just delete from it individually if possible or maybe those other 2 hosts files in that section could be used to solve?

also, how about Bluetack? 

thanks...

---

### Post by mellowchuck123 on 2011-12-29
> **bzd454 said:**
> thanks mellowchuck...

dumb question, i was wondering if there is a way to alphabetize it?  because it blocks file hosting sites and a few others that i'd rather just delete from it individually if possible or maybe those other 2 hosts files in that section could be used to solve?

also, how about Bluetack? 

thanks...

The HOSTS file is already alphabetized. If you are looking for sites to remove, Ctrl+F in gedit or whichever text editor your use, and search for the URL.

If you feel I should removed these sites, please give me a valid explanation and I will.

---

### Post by mellowchuck123 on 2011-12-29
> **bzd454 said:**
> thanks mellowchuck...

dumb question, i was wondering if there is a way to alphabetize it?  because it blocks file hosting sites and a few others that i'd rather just delete from it individually if possible or maybe those other 2 hosts files in that section could be used to solve?

also, how about Bluetack? 

thanks...

What about Bluetack? You mean bluetack.co.uk right? They have a HOSTS file now?

---

### Post by bzd454 on 2011-12-30
ok thanks....i must have merged it incorrectly or something...i was trying to get to some run of the mill file site like filefactory or filestube, then i tried to check the hosts file and it was A to Z for about 1/10th of the file or so and then started at A again so i gave up...i didn't know i could have searched with ctrl-f...    on bluetack, i was just glancing at their forum and it seemed to mention a hosts file here and there but sounds like you are already aware of them...

---

### Post by chickenPie4breakfast on 2012-02-14
Thanks MelloChuck 123  It's great of you to take the time to post these for the rest of us.

a question though, is it alright to have a few web addresses in one line like you do or have I downloaded it wrong somehow?

example line
```
0.0.0.0 www.trafficid7806.info www.tresorparis-uk.com www.tunnelingchina.com www.uberwarez.info www.uggaustraliaitalias.com www.uggbootsdeutschlands.com www.uggsshoponlineitalia.com www.uggssitoufficiale.com www.ummuclothing.com
```

---

### Post by mellowchuck123 on 2012-02-14
> **chickenPie4breakfast said:**
> Thanks MelloChuck 123  It's great of you to take the time to post these for the rest of us.

a question though, is it alright to have a few web addresses in one line like you do or have I downloaded it wrong somehow?

example line
```
0.0.0.0 www.trafficid7806.info www.tresorparis-uk.com www.tunnelingchina.com www.uberwarez.info www.uggaustraliaitalias.com www.uggbootsdeutschlands.com www.uggsshoponlineitalia.com www.uggssitoufficiale.com www.ummuclothing.com
```

Hello chickenPie4breakfast,

The script I use optimizes the HOSTS file and that is one of the results; however, I saw it as well and have tested the sites still block. You can as well and correct me if I am wrong.

Thanks.

Thank you,
mellowchuck123

---

### Post by mellowchuck123 on 2012-02-14
[CENTER]_[SIZE=4]**February 14, 2012 HOSTS file.**[/SIZE]_



** This is a combination of 9 up-to-date(as of this moment) lists that       block  ads and sites with malwares(viruses, trojans, worms etc.)**

**LISTS USED -**
[/CENTER]
       [CENTER] ```
http://www.mvps.org/winhelp2002/hosts.zip

http://hphosts.gt500.org/hosts.zip

http://updates.it-mate.co.uk/updates.asp

http://hosts-file.net/ad_servers.asp

http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts&showintro=1&mimetype=plaintext

http://someonewhocares.org/hosts/hosts

http://support.it-mate.co.uk/downloads/HOSTS.txt

http://hostsfile.mine.nu/Hosts

http://www.securemecca.com/Downloads/hosts.txt
``` [/CENTER]
 [CENTER]**The file is optimized, sorted & is in 0.0.0.0 format.**

** MAKE SURE YOU COPY THE ENTIRE FILE TO /etc/hosts using root or sudo.**

** _DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-**

** 127.0.0.1    localhost**
** 127.0.1.1    YOUR HOST NAME GOES HERE**


** If you already have blocking entries, add this list to the bottom of your hosts file.**

[SIZE=4][U][I][B]February 14, 2012 HOSTS file link:

[/B][/I][/U][https://ubuntuone.com/4iB1gOHsdbyxyMAONWZvhW](https://ubuntuone.com/4iB1gOHsdbyxyMAONWZvhW)[/SIZE]


Side note- You might want to install an ad-blocking   extension in your    browser so you don't see the annoying "page not found"   error where   ads  were before.[/CENTER]

---

### Post by bzd454 on 2012-02-22
does anyone know of a Hosts file manager for Ubuntu like HostsMan in Windows?  i'm just looking for something that i could turn it on/off very easily without having to go thru the terminal so that i could allow a webpage here and there.  i'm not too knowledgeable in linux.

---

### Post by mellowchuck123 on 2012-02-25
> **bzd454 said:**
> does anyone know of a Hosts file manager for Ubuntu like HostsMan in Windows?  i'm just looking for something that i could turn it on/off very easily without having to go thru the terminal so that i could allow a webpage here and there.  i'm not too knowledgeable in linux.

The only program I know is pup advert-block for Puppy Linux. Maybe you can compile it from source/port it to Ubuntu?

[http://murga-linux.com/puppy/viewtopic.php?t=59290](http://murga-linux.com/puppy/viewtopic.php?t=59290)

---

### Post by bzd454 on 2012-03-06
> **mellowchuck123 said:**
> The only program I know is pup advert-block for Puppy Linux. Maybe you can compile it from source/port it to Ubuntu?

[http://murga-linux.com/puppy/viewtopic.php?t=59290](http://murga-linux.com/puppy/viewtopic.php?t=59290)

thanks for the response. Compiling is beyond my knowledge though.

 i'm just trying to find something easy that would allow me to load up all these hosts file blocking lists as well as all the ABP blocking lists and malware lists etc and then when i visit a site and it doesn't work, be able to whitelist it and keep that whitelist when i update the blocking lists every month or so. and blocking all of china and russia would help i've heard. i'm not really sure the best way to do this though - maybe a firewall or the privoxy program would be better?

---

### Post by mellowchuck123 on 2012-03-25
[CENTER]_[SIZE=4]**March 25, 2012 HOSTS file.**[/SIZE]_



** This is a combination of 13 up-to-date(as of this moment) lists that     block  ads and sites with malwares(viruses, trojans, worms etc.)**

**LISTS USED -**

```
http://www.mvps.org/winhelp2002/hosts.zip

http://hphosts.gt500.org/hosts.zip

http://updates.it-mate.co.uk/updates.asp

http://hosts-file.net/download/hosts.zip

http://hosts-file.net/hphosts-partial.asp

http://hosts-file.net/ad_servers.asp

http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts&showintro=1&mimetype=plaintext

http://someonewhocares.org/hosts/hosts

http://support.it-mate.co.uk/downloads/HOSTS.txt

http://hostsfile.mine.nu/Hosts

http://www.securemecca.com/Downloads/hosts.txt

http://sysctl.org/cameleon/hosts.win

Spybot S&D Hosts Immunization
```

**The file is optimized, sorted & is in 0.0.0.0 format.**

** MAKE SURE YOU COPY THE ENTIRE FILE TO /etc/hosts using root or sudo.**

** _DO NOT_ REPLACE THE FIRST TWO LINES IN YOUR HOSTS FILE-**

** 127.0.0.1    localhost**
** 127.0.1.1    *YOUR HOST NAME GOES HERE***


** If you already have blocking entries, add this list to the bottom of your hosts file.**

[SIZE=4]_***March 25, 2012 HOSTS file link:***_

[/SIZE][SIZE=4] [_*** https://ubuntuone.com/0QsGWlv5mJ1jzRTBZuhOlr***_]("https://ubuntuone.com/0QsGWlv5mJ1jzRTBZuhOlr")
[/SIZE]
[U]
:guitar:
Side note- You might want to install an ad-blocking   extension in your  browser so you don't see the annoying "page not found"   error where ads  were before.[/U][/CENTER]

---

### Post by Sadi58 on 2012-04-03
Thanks...
Is there a way of getting "Spybot S&D Hosts Immunization" list from a permanent online address like others?
In this way, this compilation could be done automatically.
Or perhaps you might post this compiled hosts file to somewhere with a permanent address/link to save the extra effort of announcing every update.
Regards,
Sadi

---

### Post by Grandma_DOG on 2012-05-20
Can a webpage using javascripts detect if you've blocked their ads  via hostfile ?  Will there be a line of countermeasures developed for people like us?

---

### Post by Sarys on 2012-07-17
one question you said I should backup things? How?

---

### Post by Magnetizer on 2012-07-19
Hello everybody,

I just wrote my own script that can check if one of the hostfiles is updated, automatically download the hostfiles from different places, merge them, undupe them, optimize them etc. and install the hostfile on your system.

After the script is finished you get an email with the difference between the old and the new hostfile. The script also makes a backup of your old hostfile. If anything goes wrong the script stops and you will get an email with the appropriate error message.

So far, the script works nicely but it is still in beta. Right now I use it for the hostfiles from:

[http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)
[http://winhelp2002.mvps.org/hosts.txt](http://winhelp2002.mvps.org/hosts.txt)

but I will add other hostfiles aswell.

If you guys are interested I will post the script here.

Just let me know.

@mellowchuck123 your list of 13 hostfiles is quite impressive. Do you also have the URLs to the text/html version of those files?

Ot course, I could extend the script that it can handle .zip files but less work is more time for other things...;-)

---

### Post by Magnetizer on 2012-08-27
Hello everybody,

Here is the thread where I posted the script:

[http://ubuntuforums.org/showthread.php?t=2048812](http://ubuntuforums.org/showthread.php?t=2048812)

It now uses 11 different blacklists to create a the hostsfile.

I hope it is useful to some of you.

---

### Post by XxionxX on 2012-10-26
How did you make that script? It would be really cool to make my own.

---

### Post by Magnetizer on 2012-10-27
Hi XxionxX,

What should I say?

I just thought about the problem and wrote the script from scratch in 'Perl' with 'vim' as my favourite editor.

Perhaps you have a specific question you would like me to answer? If so, just ask.

As a start, just have a look at the script. You can just download the last .zip file from:

[http://ubuntuforums.org/showthread.php?t=2048812](http://ubuntuforums.org/showthread.php?t=2048812)

The script is just a textfile that you can open. Then you can see if you can understand it. It is fairly staightforward and there is some inline documentation, so I hope it is self-explanatory.

I doubt it is really useful to recreate the script except if you have a better idea. The script is open-source and licensed under the GPL, so feel free to check it out, change it, give it to your friends and so on.

If you have any suggestions, just let me know.

I hope this is an answer to your question.

Kind regards,

Magnetizer

---

