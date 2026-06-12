---
title: "Is it safe to backup the Firefox profile (.mozilla) on Dropbox ?"
date: 2014-09-21
forum: Security
---

### Post by linuxyogi on 2014-09-21
Hi,

Do you think its safe to store the .mozilla folder on Dropbox ? 

I am asking coz it has all my saved usernames and 

passwords but I have created a master password without

which the database cannot be unlocked AFAIK.

Please share your views.

---

### Post by TheFu on 2014-09-21
Don't store anything inside a browser that you don't want the entire world to see/have access with. Especially not passwords. This has been an unfixed issue for 15 yrs and still exists today.

If you care about security at all, use a password manager tool and I'd avoid any of those tools that have a browser addon ... there are security issues with addons running inside the browers ... seems there are ways for other addons to see everything.  OTOH, convenience may overrule any security considerations.

I use keepassx on Linux, keepass v1.x on Windows and keepassdroid on Android - these all work with the same DB file, though I still won't use dropbox for anything I didn't want public to the entire world.  Using rsync to mirror the password DB to all those platforms is trivial (for many people). I consider the Linux version to be the MASTER, all other locations are read-only - for reference only - in my mind. Of course, nothing prevents modifying the DB on any platform, but since the rsync push happens automatic every night from the MASTER, I need to ensure any changes are there before that time.  It is usually easier just to no make changes except on that machine (secure remote desktops work nicely for that).

---

### Post by linuxyogi on 2014-09-21
I use keepassx too. Problem is some websites do not allow persistent logins 

and I have seen that the auto type feature of keepassx doesn't always work but yes 

those sites are very few in number. 

You said that you use keepassx on Linux, Windows and Android and you haven't

faced any compatibility issues. 

That's because your master database was created with keepassx1.

Try creating a database with keepassx2 and then opening it it ver 1. It won't 

recognize the database.

When I started using keepassx I was using openSUSE and they had already

pushed keepassx2 in the default repos. I simply created a database without

realizing the complications that I will have to face if I switch distro.

By default Ubuntu has keepassx1 in the repos and I use [this PPA]("https://launchpad.net/~keepassx/+archive/ubuntu/daily") to 

install ver 2.

I am deleting all passwords stored in FF now.

---

### Post by TheFu on 2014-09-21
v2 Keepass existed, but it uses mono, which I avoid. When that shows up in a dependency, I cancel and do not install the program. KeePass v1 is still available.

A conscious decision for the version of keepass/x is all this required.  I'd be surprised if exporting the DB from v2 couldn't be important (with minor filtering) into v1 keepassx db.

---

### Post by linuxyogi on 2014-09-22
> **TheFu said:**
>  I'd be surprised if exporting the DB from v2 couldn't be important (with minor filtering) into v1 keepassx db.

It seems its not possible. Once you create a database with ver 2 you are stuck with it.

[IMG]http://s24.postimg.org/edav8x0xx/Menu_001.png[/IMG]


[IMG]http://s27.postimg.org/amt1j7ozn/Menu_001.png[/IMG]


It allows to export to a ver 2 database only. When I click on the file type option there is no other format to choose.

---

### Post by TheFu on 2014-09-22
a) that sucks. In keepassx, I have export to .... CSV or XML file options.
b) See that button "KeePass 2 Database", just above the "SAVE" button?  Can you change that?

---

### Post by linuxyogi on 2014-09-22
> **TheFu said:**
> See that button "KeePass 2 Database", just above the "SAVE" button?  Can you change that?

No, it has no other options. I don't know why they have given those tiny arrows. 

Most password managers I know including LastPass lets you export to at least xml.

I guess this move is due to some weird thinking to preserve user base.

---

### Post by TheFu on 2014-09-22
I'd dump that program immediately.

Who's data is it?  Theirs or yours?
Perhaps the compatible Windows version will export to CSV or XML?

---

### Post by matt_symes on 2014-09-22
Hi

Personally when i backup sensitive data to the cloud, i use encfs to encrypt it first and then i sync the encrypted data.

This includes my Firefox profiles - i have a number for different work flows and with different extensions enabled.

It means i cannot search for items in the cloud but i do not use the cloud as my main backup, only as my backup of last resort.

I follow the 3-2-1 method for backing up my data and my main backups are in-house with my cloud backup as, as i said, the backup of last resort.

EDIT: As I'm not so much worried about mono, i use keepass2 but i understand why people are uncomfortable using mono.

EDIT: Incidentally, I use incremental rsync backups and these backups also get backed up.

Kind regards

---

### Post by Dragonbite on 2014-09-22
What about just setting Firefox to sync?  Then if you have a 2nd computer you set that one up to sync as well and everything can be in both places.

Then again, I haven't managed to get Firefox to sync successfully yet, but I always have problems with computers (like the entire button the documentation says ot press is missing... things like that )

---

### Post by linuxyogi on 2014-09-22
> **TheFu said:**
> I'd dump that program immediately.

Who's data is it?  Theirs or yours?
Perhaps the compatible Windows version will export to CSV or XML?

I just tried 2 password managers. The first one is called Figaro's Password Manager. This time I wanted to make sure it can export  to generic formats and I found it can I was filling up my login details one by one.

After completing like 20-25 entries  I thought lets check if this app actually works and I found that despite the fact that the passwords are getting saved when I try to copy and paste them it wont work. It can only copy the usernames !!! 

Now the second one is called Password Gorilla and it can export the database to .csv and .txt. This one actually works. 

I have copied the important / most visited logins first. Frankly its a very boring task and copying all in one sitting won't be

possible. I guess I will complete the transfer within 3-4 days.

> **Dragonbite said:**
> What about just setting Firefox to sync?  Then if you have a 2nd computer you set that one up to sync as well and everything can be in both places.

Then again, I haven't managed to get Firefox to sync successfully yet, but I always have problems with computers (like the entire button the documentation says ot press is missing... things like that )

I have only one PC atm. Usually I don't need to back up large amounts of data otherwise an HDD is the best option IMO.

I only backup my docs, photos, and  a part of my music collection which is quite small in size. What I do is once it reaches 

650+MB I burn it to a CD.

> **matt_symes said:**
> Hi
Personally when i backup sensitive data to the cloud, i use encfs to encrypt it first and then i sync the encrypted data.


I hope there will be a easy to use GUI frontend for encfs soon till then I will backup my FF profile to my USB flash drive.

---

### Post by linuxyogi on 2014-10-19
> **TheFu said:**
> a) that sucks. In keepassx, I have export to .... CSV or XML file options.
b) See that button "KeePass 2 Database", just above the "SAVE" button?  Can you change that?

Yesterday I was searching like crazy for a way to export my KeePassX2 database to a plaintext 

format and what found is that KeePassX is nothing but a fork of KeePass.

A database created with KeePassX2 can be opened will KeePass and KeePass allows exporting to

other formats. So from now on I will use KeePass.

[ATTACH=CONFIG]257341[/ATTACH]

Click to enlarge.

I have started using encfs to encrypt my dropbox data.

---

### Post by markodd on 2014-10-19
linuxyogi, I haven't read all the replies from this thread so I apologize if what I'm about to say has been said already (do people read all the replies when joining a thread?).


I suggest using lastpass for internet accounts that are not too important (such as forum account and such) and keepassx for bank stuff and paypal and the likes. Before doing this, please have in mind that LastPass is an US based cloud solution. You might not be comfortable with that. Read more about lastpass and make your decision (they say they've no access to user's information, as it features client's side encryption but still..)


If you do decide to use LastPass, you won't have to store passwords in firefox. Honestly, LastPass is an absolutely fantastic piece of software. I've premium of it even though I don't need. I've no weak passwords now!


If you do decide you want to upload Firefox' profile in the cloud follow this word of advice:


[CENTER]**Never store anything in the cloud without first encrypting it.**[/CENTER]

---

### Post by linuxyogi on 2014-10-19
> **markodd said:**
>  If you do decide to use LastPass, you won't have to store passwords in firefox. Honestly, LastPass is an absolutely fantastic piece of software. I've premium of it even though I don't need. I've no weak passwords now!


I tried using LastPass twice but for some reason it didn't work for me.

I created an account, saved some sites (using the same passwords which were stored in KeePassX).

Then I installed a new distro and logged into my LastPass account using my email id as username

and my master password but I found that the password vault was completely empty.

This same problem has happened twice. 

Yes, I did not save my banking, paypal or even online shopping passwords.

---

### Post by markodd on 2014-10-19
> **linuxyogi said:**
> I tried using LastPass twice but for some reason it didn't work for me.

I created an account, saved some sites (using the same passwords which were stored in KeePassX).

Then I installed a new distro and logged into my LastPass account using my email id as username

and my master password but I found that the password vault was completely empty.

This same problem has happened twice. 

Yes, I did not save my banking, paypal or even online shopping passwords.

That is very very weird... Go to their forums and ask what happened. If I were you, I'd try another time. You're losing a wonderful piece of software.

---

### Post by linuxyogi on 2014-10-19
I installed LastPass again, logged in and after a lot of searching found that that my saved sites 

have moved to the [COLOR=#006400]*deleted items*[/COLOR]. Available options are purge and undelete so I clicked undelete

on each saved site. Now both *[COLOR=#006400]my vault[/COLOR]* and *[COLOR=#006400]deleted items[/COLOR]* pages are empty !!!

Thanks to local database I won't have reset all those passwords.

Edit : There's some issue with the plugin coz when I login to their web interface

I see all my saved sites,

---

### Post by markodd on 2014-10-19
That is weird. I've never had such a problem. Have you tried re-installing the plugin? Install it from their site, as it's the latest version there, which might not be true for the firefox extensions page.

I'd just like to mention that what's happening to you is not normal behaviour, at all... Please don't base your entire opinion on LastPass based on what's happening to you! Try to fix that issue and you'll see the magic of lastpass.

---

### Post by linuxyogi on 2014-10-19
> **markodd said:**
> That is weird. I've never had such a problem. Have you tried re-installing the plugin? Install it from their site, as it's the latest version there, which might not be true for the firefox extensions page.

I'd just like to mention that what's happening to you is not normal behaviour, at all... Please don't base your entire opinion on LastPass based on what's happening to you! Try to fix that issue and you'll see the magic of lastpass.

Actually I had uninstalled LastPass some months backs when I faced this issue. 

So, this is a fresh install anyways. 

Good news is LastPass is working fine with Firefox Aurora so the problem is 

not with the plugin but the Firefox version under which I was trying LastPass.

Let me explain, I have 2 VirtualBox VMs atm. Debian 7 Wheezy and OpenBSD.

Both are in bridged networking mode. I don't do any Internet activity on the host.

I have done port forwarding on the Wheezy install for torrenting. 

I installed OpenBSD just out of curiosity coz I was reading all over the web that

its hardened by default. I have no knowledge about penetration testing. All I can

do is enable ufw and then run nmap <IP address> and check if a port is open.

If I see any unnecessary service listening to a port I simply uninstall the package 

altogether. In case of OpenBSD PF is installed and enabled by default with a 

strict policy. Nmap can't even run a scan.

The only issue that I see with OpenBSD is that the packages in their repos are

very old. They don't upgrade, they only apply security patches. I mean there 

is no major change in versions for long long time.

The downside to this is some of the addons become incompatible after a certain

period. 

As you know I maintain a local database with KeePass so the only use of LastPass to

me is access to passwords inside my VMs. KeePassX(1) is available in their repos

but not KeePass. So I guess the only remaining option is to use LastPass's web interface

to copy/paste the passwords. Most sites allows persistent logins so I guess I will be able

to manage.

Sorry for the confusion.

---

### Post by jeehyun on 2014-10-19
What about using MEGA cloud for critical files. It supports encryption and based on New zealand and Germany.

---

### Post by TheFu on 2014-10-19
> **jeehyun said:**
> What about using MEGA cloud for critical files. It supports encryption and based on New zealand and Germany.

I've learned to never believe any website's claims about their implementation of encryption. It is just too easy to make a tiny mistake that completely removes all the security.  I've never seen any quaranty from these websites about their encryption either.  Most seem to let marketing people create the info on the website about their encryption  - marketing people NEVER overstate anything after all. ;)  Usually, the truth gets oversimplified to the point of being untrue or completely worthless to know if there is any real security at all.

Best to pre-encrypt any data before placing anything anywhere public (i.e. on someone elses computer) with tools YOU trust if you don't want it be leaked.  Oh - and don't trust any encryption implemented inside a browser, please.

---

### Post by Penguin360 on 2014-10-20
When it comes to backing up sensitive data to cloud, it can never be too paranoid about the security and privacy, so encrypt your data then back up to the cloud if you choose to. 

Personally, I never back up my passwords to cloud.

---

