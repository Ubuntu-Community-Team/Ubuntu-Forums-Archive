---
title: "laptop loss best strategy"
date: 2009-11-29
forum: Security
---

### Post by dgermann on 2009-11-29
Hi--

Have a continuing education seminar to attend this week which is "paperless"--so I need my laptop to read the pdf handouts. What are the best ways to protect my laptop while in this public setting with people coming and going for two days?

I see three issues, but perhaps you see more:

1. I have a Kensington lock which I can try to use to lock my laptop to the 6 foot tables the conference center provides.

2. My data is important. I think there are programs that can be activated to completely nuke the hard drive if the laptop is lost or stolen. What's the best of the best out there for linux?

3. Locating my laptop itself would be a good thing. I saw yesterday something about [http://preyproject.com/]("http://preyproject.com/") which I suspect is one of many such. What's the best of the best out there for linux?

Thanks!

---

### Post by tubbygweilo on 2009-11-29
Doug,
Don't let your laptop out of your sight, treat it as you would your  wallet, keys and credit cards as this should thwart most physical attacks and people messing with your stuff or your data.

Think about protecting data by encrypting with something like [Truecrypt]("http://www.truecrypt.org/faq").

I am sure others will have lots to add, hope it all goes well.

---

### Post by OpSecShellshock on 2009-11-29
If it's possible, try to have a separate machine for travel that has less stuff on it. If that's not going to be an option, I'd recommend going through the data on the hard drive, keeping only what you absolutely need for these seminars, and then back everything else up to an external storage device and leave that at home. There is less risk to the important data if it's not on the machine at all.

Make a note of the manufacturer, model number and serial number of the hardware, just in case. Then, of course, do not, under any circumstances, leave the laptop unattended. Take it with you to lunch. If you must leave it at the hotel, get a safe behind the front desk (not in the room). Make sure that the desk staff knows that they need to ask for your ID to get it back since there will be shift changes.

---

### Post by movieman on 2009-11-29
At the least, ensure that the home directory is encrypted and use a strong password; then if it is stolen they won't be able to read any important files.

Also, you might want to consider buying a cheap netbook and only taking what's essential for the trip, so that if it is lost you won't have to worry so much.

---

### Post by dgermann on 2009-11-29
tubbygweilo--
OpSecShellshock--
movieman--

Thank you each for helping me.

It is interesting to me that none of you have suggested any software to locate the lost computer or delete the drive.

Physical control is of course the strongest safeguard, and I am working on having a lightweight case with a shoulder strap so I can carry it around. Encrypting the drive makes sense to me, too. What kinds of options are available for that? I'm a little nervous about putting something on top of the OS that might get messed up on apt-get upgrades.

I see in synaptic these apps--are any of them a good bet for encrypting a drive or directory? Seahorse; encfs; easycrypt (based on your suggested truecrypt); cryptmount; cfs; ccrypt; bcrypt. Any suggestions which is easiest and safest for a encryption neophyte? (I consider myself capable of doing many command line things, but have not gone as far as compiling a program, nor a kernel).

Oh, and are there other options for reading a PDF file, short of taking a computer or netbook?

Thanks!

---

### Post by movieman on 2009-11-29
I don't really know of any programs for tracking the laptop, but I guess you could always have it send a message somehow (email, web access, etc) when it's turned on so that you know the IP address it's using.

Ubuntu has ecryptfs built in which seems to work well: it encrypts the files in your home directory with a random key and then encrypts the key with your password, so you can't even see the files if you can't log in.

I'm not sure of the official method of enabling it on an existing user account, but it's a flag you can enable when creating new accounts. Just back up the unencrypted files beforehand in case something screws up... you won't be able to read them either if you lose the password :).

---

### Post by dgermann on 2009-11-29
movieman--

Thanks!

Is ecryptfs the same as encfs? I do not get any man page for encryptfs, nor is there any entry in synaptic for it.

I'm using 8.04.1 lts--maybe that is the difference. I see you're using 9.10.

Thanks, movieman!

---

### Post by XCan on 2009-11-30
> **dgermann said:**
> tubbygweilo--
OpSecShellshock--
movieman--

Thank you each for helping me.

It is interesting to me that none of you have suggested any software to locate the lost computer or delete the drive.

Physical control is of course the strongest safeguard, and I am working on having a lightweight case with a shoulder strap so I can carry it around. Encrypting the drive makes sense to me, too. What kinds of options are available for that? I'm a little nervous about putting something on top of the OS that might get messed up on apt-get upgrades.

I see in synaptic these apps--are any of them a good bet for encrypting a drive or directory? Seahorse; encfs; easycrypt (based on your suggested truecrypt); cryptmount; cfs; ccrypt; bcrypt. Any suggestions which is easiest and safest for a encryption neophyte? (I consider myself capable of doing many command line things, but have not gone as far as compiling a program, nor a kernel).

Oh, and are there other options for reading a PDF file, short of taking a computer or netbook?

Thanks!

Even though I don't doubt your cli skills, I would still recommend you to go with truecrypt. It comes with a gui, thus I don't know what the deal is with easycrypt, and is extremely easy and fast to use. In addition, it works great from the command line, which I use on a regular basis to run my mount scripts. 

Reading pdf files without a netbook or notebook can be achieved with certain smartphones or one of those ebook readers. :)

---

### Post by BkkBonanza on 2009-11-30
The way I see it once your laptop is stolen you can forget about getting it back. Chances are slim at best. Any thief is likely to wipe it all out and install Windows anyway, and if they do go looking for data the only data that matters is stuff that could cause you grief or embarassment.

What you want to do is protect data that could be used by someone maliciously against you. Usually this just means a fairly small subset of all the data onboard. Things like passwords, server keys, credit card info, documents with sensitive info / business details etc.

I would use truecrypt to create a volume file big enough for your sensitive data. Mount the volume somewhere in your home, and move the sensitive data to that location. Unmount that volume whenever you are not directly using it. Don't write down the password for that volume where a thief may find it. After moving it be sure to "shred" the original copies so they don't exist in the free space after moving. (read "man shred")

The rest of the files on your system aren't worth protecting and encrypting the whole drive / filesystem is a lot of work to protect what few files are important for most users.

If you have keys for access to other servers/machinse on you keyring in home then you may want to think about them. Either arrange for them to be on the encrypted volume as well (perhaps move them and add symlink to them), or make sure if your laptop does get stolen to have those keys removed immediately from any servers they access.

If you have a passwords file that's not encrypted make sure it's in the encrypted location or use something like KeepassX (in the repos).

Truecrypt is quite easy to use and known to have solid encryption not accessible by someone gaining root on your laptop. (Anyone stealing it can be assumed to gain root as soon as they boot from a live cd). I think Truecrypt is in Synaptics and it's GUI is easy to use and sensible.

---

### Post by EJeanmaire on 2009-11-30
> **dgermann said:**
> tubbygweilo--
OpSecShellshock--
movieman--

Thank you each for helping me.

It is interesting to me that none of you have suggested any software to locate the lost computer or delete the drive.

Physical control is of course the strongest safeguard, and I am working on having a lightweight case with a shoulder strap so I can carry it around. Encrypting the drive makes sense to me, too. What kinds of options are available for that? I'm a little nervous about putting something on top of the OS that might get messed up on apt-get upgrades.

I see in synaptic these apps--are any of them a good bet for encrypting a drive or directory? Seahorse; encfs; easycrypt (based on your suggested truecrypt); cryptmount; cfs; ccrypt; bcrypt. Any suggestions which is easiest and safest for a encryption neophyte? (I consider myself capable of doing many command line things, but have not gone as far as compiling a program, nor a kernel).

Oh, and are there other options for reading a PDF file, short of taking a computer or netbook?

Thanks!


The sticky at the top of this section covers step-by-step directions to multiple different encryption options.  Whichever you pick make sure its full disk encryption.

Secondly, back up your important files to a secure location (not to be taken with you to the conference) in case your laptop is in fact stolen. 

Use your cable lock on to secure the laptop to bolted down desks, tables. 

Make sure you lock the laptop to screensaver/login window every time you walk away from it.  Best would be to power it down so that nothing is loaded into memory.

Set a password on the BIOS of your computer.

Lastly, forget about tracking it unless it has GPS built in.  The encryption will hold on the harddrive for many many years to come if adequate algorithms are used.

---

### Post by pbrane on 2009-11-30
If you happen to have a Dell laptop,
[http://www.dell.com/content/topics/global.aspx/services/prosupport/computrace?c=us&l=en&cs=555]("http://www.dell.com/content/topics/global.aspx/services/prosupport/computrace?c=us&l=en&cs=555")

otherwise you might find out if this type of option is available for your laptop.
I have a Dell laptop and saw the option to enable something like this in the BIOS.

---

### Post by dgermann on 2009-11-30
XCan--

Thanks for helping me. 

I will check into TrueCrypt. The one tutorial I found makes it sound difficult.

A netbook I am guessing will need internet access and in the facility where I will be that is sold by the minute! (I know, sounds like the 1980s when I first logged into Compuserve with a 2400 baud modem.) So that is probably out. ;)

BkkBonaza--

Sadly, I think you are right about recovering the laptop.

I like your idea about the keys and about encrypting just a small part of the drive. Smart!

Thanks!

EJeanmaire--

Great ideas! Thanks. 

If I set a bios password, that still does not protect me if someone physically removes the hard drive, right?

pbrane--


Happily, mine is a System76. I will check there to see if they have something already built in.

Thanks!

---

### Post by BkkBonanza on 2009-12-01
Most of these ideas are good any time - you never know even on your average day when your laptop could be stolen. How seriously you take the encryption route depends on just how dangerous it would be if you lost data.

A BIOS password won't help at all if someone steals your laptop. They can reset the CMOS and gain access, and they can remove the drive and look at it on another computer. It pretty much just prevents someone getting in when they can't take it away or don't want to let you know they subverted it.

It's been a long time since I installed Truecrypt but I think you can just select it in Synaptics and a few clicks hsould get it installed. Then you will find it in the Menu: Applciations, Accessories. You start it and choose the option to create a new volume and tell it how big. Follow the step-by-step and it creates a volume file. Then you choose the "Mount" option to mount the volume at some location. So you may want to make a folder in your home called whatever, say, "Docs", and you can choose to mount the volume there eg. mount at /home/doug/Docs. It will ask for the password of course, and then mount it for you. Anything you copy into that folder now goes into the volume and not the normal hard drive. After your'e done you click Dismount to lock the volume and remove it from the mount point. It is fairly easy after you work your way through it the first time.

Note that other users here are correct that for maximal security a whole encrypted drive is best but I realize that is a major system change at this point and probably not something you want to do just before hitting the conference, or even at all. 

Keep in mind a few things. When using documents from an encrypted volume some programs will create temporary files and use swap space where copies of the data could be duplicated. When finished working, or reading, those fragments can still exist. So even with an encrypted volume it is possible for information to leak and it really depends on your level of paranoia, and just how hard some thief is expected to work to gain your information. In mosts cases it isn't a big deal but in some cases where the value is high, and cost of an information leak high, you would want to move to this higher level. 

The best solution is to not have critical data in a location where it could be lost.

---

### Post by movieman on 2009-12-01
> **dgermann said:**
> A netbook I am guessing will need internet access and in the facility where I will be that is sold by the minute!

A netbook is basically a small, low-powered laptop. Originally they were designed with minimal local storage and heavily reliant on Internet access, but over time they've tended towards 100-200GB hard drives so you can carry a fair amount of data with you.

So a bigger question would be whether the screen is large enough to display your files adequately. Typically you'll get about 1024x500 pixels for an application window once you take account of toolbars, etc.

---

### Post by dgermann on 2009-12-01
movieman--

Ahh! That might mean netbooks would be worth looking into. Thanks.

BkkBonaza--

TrueCrypt is not in the repos on 8.04.1, but there is a .deb from their site which I have downloaded. Now, if I can find time tonight to see if I can install it.... That ought to be easier than the tutorial I had found which talked about make, make install, etc.!

You are right that I do not want to do a whole system change overnight. What I am thinking of is encrypting my home directory. What I think that means is that I cp home someplace else, then shred the stuff in there, and then make a new mount point within that directory and cp back all the stuff. Then shred the copied directory contents. That sound about right?

Also, I found a poor man's linux approach to lojack involving ddclient and dynDNS here: [http://www.helium.com/items/353689-how-to-set-up-a-lojack-for-your-linux-computer]("http://www.helium.com/items/353689-how-to-set-up-a-lojack-for-your-linux-computer") Any thoughts on that?

I value your opinions--you seem to have an in-depth practical approach. Thanks, BkkBonaza!

---

### Post by BkkBonanza on 2009-12-01
You shouldn't need to copy home twice. I don't know if I'd make my whole home a truecrypt volume. Perhaps that will work but I suspect there may be a problem booting/logging in if the volume can't be mounted before authentication. It may work but I have never done that.

Once you have the deb file you should be able to right-click it and select "Deb Package Install" (or something like that, can't recall actual wording). That will install the deb pretty much the same as from Synaptics with the exception that it won't handle automatic updates for it. Until you update Ubuntu this is ok because the deb pkg is likely more up to date now anyway. (You're right you don't want to build from source with make etc.)

Here is how I would do the copy and replace of home...
Once you have created a truecrypt volume - mount it somewhere outside /home/doug like /home/tmp maybe. Then copy all of your /home/doug to that place. Test it out a bit to make sure you didn't do something wrong and it works. Unmount it and remount it to confirm to yourself what you have is working. Then you would rename your /home/doug to /home/doug.bak and mkdir a new doug and mount the truecrypt volume there. A truecrypt volume can be mounted in different places as needed. After the truecrupt one is mounted and working (test some apps), then you can shred the doug2 one finally. 

Regarding the Lojack idea. This ddclient/dyndns setup is commonly used to run servers on adsl home lines. It works and what he describes should work... as long as the thief doesn't wipe your system. In my opinion the chance of that is pretty slim. I suppose you could get a hit once or twice even before it gets wiped if they're silly enough to connect to the net before wiping (or even see ddclient and disable it). I may be smarter than you average thief but I'd survey the system thoroughly before connecting to the web.

This method is a bit round-about though. You could achieve the same thing by adding a small script to the /etc/cron.daily directory. Scripts in there get called each day by anacron (so they get called sometime after booting if it's been more than a day). The script would use wget to hit a website like whatismyip.com and email the received info to your email. Of course, it would do that always, even before it gets stolen (once each day). Such a script would be pretty simple, even one line like:

wget -O - whatismyip.com | mail -s "laptop location" [email]thatsme@somewhere.com[/email]
(or instead of whatsmyip it could do a traceroute, and this assumes mail command is working - often it's not)

My guess is that a thief with a linux laptop will give it someone who will put windows on it to sell. Or who knows.

---

### Post by tubbygweilo on 2009-12-01
> My guess is that a thief with a linux laptop will give it someone who will put windows on it to sell. Or who knows.
I fear a thief will on discovering that he has not a windows flavoured laptop will then trash it and bin it because to do anything else will take time and may not be considered a good return on his efforts. 

Master Po: "Grasshopper, It is better you don't let the kit out of your sight in the first place".

---

### Post by dgermann on 2009-12-01
tubbygweilo--

You're probably right!

BkkBonaza--

I tried your command line prior to creating an anacron script, but I am doing something wrong. It is not sending the email to me. I first installed mailx. Then used your script but on [http://noc.net.umd.edu/cgi-bin/netmgr/whoami]("http://noc.net.umd.edu/cgi-bin/netmgr/whoami"). It seems to run through getting the info OK, but does not mail anything. Any ideas? Do I have to send through another mail account somehow? Do I have to install something else, like sendmail? (Don't know what that is, saw it mentioned in a google search). Or sendemail?

I did get TrueCrypt to install. Now I just need to figure it out. Could it be used for my evolution email files? Any special tricks you'd suggest for that?

Thanks for helping me.

---

### Post by BkkBonanza on 2009-12-01
Sending mail to remote domains is disabled by default on Ubuntu desktop. Exim is the replacement for sendmail and will send mail but only to local users.

I had also tested that command as well and found that mail would not send to remote domains, which is why I edited and added that note about it not working. It can be enabled though if you want to allow sending mail form the command line. I expect it was disabled for security reasons to prevent someone writing a script to send spam.

If you type "mail" you will get your user mailbox contents listed. Most people don't use this mailbox because they typically use some gui program like Thunderbird or Evolution. I know for me when I type mail from time to time to check I always have a long list of system mail from root reporting on cron jobs. So I periodically delete all these messages (the d command once in mail prompt, q will quit mail prompt).

Anyway, to enable mail to remote domains you use,
sudo dpkg-reconfigure exim4-config
and select sending mail to remote with smtp. See the note there as well that often dynamic ips are blocked my smtp servers to prevent spam. I expect there is a better way to do a scripted mail than this but I haven't looked into it (except on my web server where it does work). 

If you do enable remote smtp then you should be able to send mail using the mail command or sendmail command. With sendmail you would use -i so that with the piped data the end of data is recognized.

If you have your own website (or access to the logs of one) then an even simpler solution is to just hit some url there with wget. Any hit on the server will cause an access log entry with the IP that you can look for later. You would need to use some special url that you know to look for. This is even easier than the mail method but requires you have access to a server's logs.

---

I have not used Truecrypt for my home folder. I believe it should work but have no special tips. I use Thunderbird so for me I would create a volume to mount on /home/user/.mozilla-thunderbird - I expect there is a hidden evolution directory in your home that would be the correct one.

---

### Post by dgermann on 2009-12-01
BkkBonaza--

Ahh. Not sure I have access to logs, but I can probably get access if I need it. I do have access via ftp and DirectAdmin. With that there is an apache usage log, which has a lot of ipaddresses in the logs. Might that be the kind of logs you are suggesting? Like this: 

```
65.55.106.155 - - [01/Dec/2009:22:28:07 -0600] "GET /?m=20051111 HTTP/1.1" 200 5303 "-" "msnbot/2.0b (+http://search.msn.com/msnbot.htm)"
67.195.115.124 - - [01/Dec/2009:22:28:21 -0600] "GET /?p=2360 HTTP/1.0" 200 2275 "-" "Mozilla/5.0 (compatible; Yahoo! Slurp/3.0; http://help.yahoo.com/help/us/ysearch/slurp)"
174.37.205.91 - - [01/Dec/2009:22:28:22 -0600] "GET /?feed=atom HTTP/1.1" 200 2081 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.2.1; aggregator:Spinn3r (Spinn3r 3.1); http://spinn3r.com/robot) Gecko/20021130"
65.55.106.155 - - [01/Dec/2009:22:28:20 -0600] "GET /?m=20051111 HTTP/1.0" 200 24801 "-" "msnbot/2.0b (+http://search.msn.com/msnbot.htm)"
67.218.116.163 - - [01/Dec/2009:22:28:25 -0600] "GET /wp-trackback.php?p=5653 HTTP/1.0" 302 372 "-" "Mozilla/5.0 (Twiceler-0.9 http://www.cuil.com/twiceler/robot.html)"

```

So I was thinking ping or touch a particular file might just do as well as wget, but ping might not be logged. touch probably would be, particularly if I set it up for a certain pattern--5 times three seconds apart every hour on the X minute.

If that would work, then I'd rather not play with smtp. Would you agree?

Thanks! This is interesting stuff.

I am trying to get a truecrypt file created--first one took 68 minutes and then I had to cancel because it did not accept my password. (I think it said something about "or your administrator password"--I wonder if it wanted my normal linux user's password?) Not sure what that was about, so I am trying again.

---

### Post by BkkBonanza on 2009-12-01
Yes, if you can view that access log then using wget to hit some url would be the dead easy way and use less resources all around. Don't use ping as it won't be logged and I think touch is not preferable because it would need special access to touch a file on the server. With wget you can use a fake url that will be logged as error (no problem) and be very easy to find. I think this method is preferred to email.

cron script contains,

wget [http://myserver.com/justdougcheckinghome](http://myserver.com/justdougcheckinghome) > /dev/null

The >/dev/null sends the response (an error page) to nowhere. No need to keep it around (by default wget would put it in the file index.html).

When looking at your server log just search for "justdougcheckinghome". Or better still just use grep (requires command line access though),

grep justdougcheckinghome /var/log/whatever/access.log

Will dump the lines logged that have that string and will show the ip address.

---

When you create a truecrypt volume it will ask for a password to the volume. Make it good because guessing that is how someone could bypass the strong cryptography being used. This should not be the same as your user id in case that one gets compromised.

When you mount the volume it will ask for two passwords in turn, first the one for the volume and then the one for your userid. The second one is needed because truecrypt needs sudo access to mount the volume. If you mount more than one in a short time it won't re-ask for the user password.

... 68 minutes - wow, either a real big volume or slow computer...

---

### Post by dgermann on 2009-12-02
BkkBonaza--

Many thanks.

I am now about ready for my seminar tomorrow. I did figure out the problem with truecrypt--it was asking for my user's password so it would have admin access to create the dir (yes, it's a big directory, 25 gigs). Once I realized that, it created it fine.

I found that I could store the .evolution/mail/local directory in the encrypted volume and then ln -s to it and it seems to work seamlessly.

I am getting tired right now so I might not do the cron entry this evening, but your approach looks elegant.

Thank you!

---

### Post by dgermann on 2009-12-20
BkkBonaza--

OK, finally got around to setting this up--seems to work like a charm.

I tweaked it by adding -q to wget, since running the entry produced a response on the screen. Want to have it as hush-hush as possible.

Elegant solution, BkkBonaza! Thanks! :popcorn:

---

### Post by perrabyte on 2009-12-21
What about using striped disks, RAID 0 for security?

The idea is that you could split the data on to at least two physical volumes. Perhaps one of those being a SDHC-card which you carry with you in your wallet. This way you need both the partition in the laptop and the card to read the files. Since encryption relies on passwords and thats a weak link. Distributing the encrypted file on two physical volumes would give more security I believe. 

This not meant for long periods of use though. If you loose the SDHC-card or the SSD-partition you would not be able to restore the files.

---

### Post by BkkBonanza on 2009-12-21
@Doug,
Since those previous posts I've explored the option of using ecryptfs for an encrypted home directory. I think this has become my preferred solution for now. Mostly due to ease of use. I followed the tutorial below to convert my regular home to an encrypted version. And then I also added in a few changes so I could have some parts of my home non-encrypted.

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

The nice thing about this is that it is all handled by default on login. So no extra prompts and passwords. I still use truecrypt for special volumes I mount when I need extra security. I just feel that having home being encrypted by default protects me against people getting email, bookmarks, ssh keys and such that are available by root login with physical access.

Another nice thing is that you can copy the key at ~/.ecryptfs/wrapped-passphrase to a usb key/sd card and replace it with a symlink. This would give you **2 factor** authentication where you need your login pwd and also the usb key to get in. I like that. Then your security depends **not just on a password but a 128-bit key present** on the key. Since it's very easy to copy the file and make a symlink it would easy to setup when travelling. I'd keep a backup of the wrapped-passphrase in my Keepassx password db as well in case the key gets lost.

I'm impressed by how transparent but still secure they have managed to make this now. For a notebook situation I believe it's ideal.

More useful links on how ecryptfs home works,
[http://blog.dustinkirkland.com/2009/03/ubuntu-encrypted-home-with-2-factor.html](http://blog.dustinkirkland.com/2009/03/ubuntu-encrypted-home-with-2-factor.html)
[http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html](http://blog.dustinkirkland.com/2009/02/how-encrypted-home-ecryptfs-works.html)

---

### Post by Neezer on 2009-12-21
I had a media server at home that would check its IP address every hour and keep a record of what it is. anytime it would change, it would automatically send me an email so that I would know what its new IP address was so that I could use SSH to manage the machine while I was away.

I don't think IP address is as exact as physical address, but you might get somewhere with that.

---

### Post by dgermann on 2009-12-22
perrabyte--

Interesting. I looked at RAID 3 or 4 years ago and it seemed cumbersome (at least for me at my stage then of understanding of linux), so maybe it's worth another look now. Thanks!

BkkBonaza--

You keep a step ahead of me, don't you? ;)

That certainly bears looking into, and does not look particularly difficult to set up. Was it as easy as it looks?

Thanks!

Neezer--

What did your script look like to cause it to compare ipaddresses and then email you? That looks like a good trick to know.

I once had a person working from home and logging in from a distance. We uses a dynamic dns provider, but that was a little erratic. Your idea might be a good solution for that kind of situation, too.

Thanks, Neezer!

---

### Post by BkkBonanza on 2009-12-22
Doug,
The tutorial worked as written and was quite easy. I did make a backup of my home first just in case I messed up but it went well first time. That tutorial is written by one of the kernel developers and after reading several of his blog entries I think he knows this stuff well. Anyway, converting like this is easier then a re-install.

One thing I think would be useful in public situations would be a way to force logout or screen saver when a usb key is pulled out. I think this could be done by udev rules but I haven't looked into it (yet).

---

### Post by eddier on 2009-12-23
If your Data is critical then dont leave on the laptop,at the end of each session either dump it onto a portable (2.5") drive or a large usb stick,then delete from the laptop after verifying the backup.

Doesn't recover your laptop but your data is safe.

Use a cheap but usable laptop that is easy to replace.

Incidentally some DEll Laptops with BIOS Password protection are near impossible to crack (it isnt stored in cmos memory)-you have to contact Dell,give them the serial number of the product in Question and they will supply a backdoor password.

eddie

---

### Post by dgermann on 2009-12-23
BkkBonaza--

Let me know, please, if you figure it out.

eddier--

Thanks. That's a good idea. Of course, I would shred, not just delete! ;)

Mine's a system76.

---

### Post by BkkBonanza on 2009-12-23
I figured out how to do it using a udev rule. The problem was getting the screensaver lock command to work. It requires some finessing because the udev rule runs as root and the screensaver lock has to be run as the current user (and X session), and sometimes it seems the screensaver isn't even available. I had it working but it was quite unreliable. So I may come back to it again but for now was tired.

---

### Post by dgermann on 2009-12-23
BkkBonaza--

You're a real trouper! :guitar:

---

