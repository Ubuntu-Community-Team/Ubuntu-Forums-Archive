---
title: "[SOLVED] Question on privileges"
date: 2008-12-15
forum: Security
---

### Post by HungryMan on 2008-12-15
Hi, I was just curious about privileges. Sudo gives you the maximum rights you can have, but not necessarily root, right? I tried ```
sudo rm -r *folder*
```
on OSX on an account that is not "administrator" It did not do anything at all, not even complain that I had no rights.
Afaik, sudo does not make you root, it gives you higher privileges (based on sudoers) than you normally do, which doesn't necessarily mean root privileges. But if sudo doesn't make you root, why does XFCE warn me, "Warning, you are using the root account. You may damage your system." if I do```
gksudo thunar
```?

Lastly, since I might be securing some Windows boxes soon, is "run as..." the closest Windows can be to gksudo/kdesudo on a limited account? I've heard a rumor that Windows' privileges are not as enforced as *nix ones, and even if a limited user ran malicious code, there are ways to harm the system overall.

Thanks in advance, and sorry for being to curious :D

---

### Post by ibutho on 2008-12-15
Sudo does not necessarily give you the maximum "rights" possible. On most distributions (and the BSDs, Solaris etc), sudo is used to give some normal users, limited admin privileges (although you can configure it to give certain users superuser privileges). In some instances it may not even be installed because where one person is administering a system, its not really necessary to have sudo. On Ubuntu however, sudo is used as a way to give users in the admin group superuser privileges. The way they have set it up by default is quite different from that of other distros. XFCE was probably complaining because if you are in the admin group and you run "gksu somecommand", you are in a way running the command with superuser privileges although you are not root.

---

### Post by HungryMan on 2008-12-15
@_@ i'm confused...

sudo on ubuntu gives superuser rights, but NOT make the sudoer superuser.
so, sudo will give the sudoer the maximum rights audited to him via the sudoers file?

which explains why nothing happened at all when i did "sudo rm -rf .trashes", because at that time, I had no right to do so, whether or not i did sudo.

gaaah! i'm so confused about the concept of sudo...

---

### Post by Sarmacid on 2008-12-15
When using sudo in Ubuntu you get root permissions, check the ouput of
```
whoami
sudo whoami
```
You can even get a root shell with```
sudo -i
```

---

### Post by jdackle on 2008-12-15
A few cents worth (I hope! :mrgreen: ):

The root user in Ubuntu does exist. HOWEVER it is not allowed to login! (keep reading, this meets a point further ahead). (*CTW, I did not know you could actually run a login shell with "sudo -i" but I'll trust the word for it)*

I'll compare Ubuntu to Mandrake and Mandriva and then get back to **sudo (gksudo et al)** and **su (gksu et al)**.

I'd been using Mandrake as my main distro for years before I tried Ubuntu (only tried Mandriva (= Mandrake + Conectiva) about a month ago).
At any fresh-install of Mandrake, you'd be asked for a username and its password AND for the root password. 
Hence, by default, you'd have two users able to login with when you ran your Mandrake install for the first time, even though, depending on the Mandrake release, specifically later ones, root might not be able to login to X (using gdm, kdm, xdm, whatever) but only to the text-console (something a fresh Ubuntu install does not allow you to do).
You could then just start a login-shell (or desktop environment if the desktop manager was configured to allow it) with username "root" and root's password (you had setup on system installation) just like you'd login to any other normal-user account.

[I](I was actually pretty stunned at first to see Ubuntu ask for my "regular" user's password to run some administration program. Mandrake would always ask me for the root's password in such a situation. I still think Mandrake's aproach was more secure than Ubuntu's on this but I think it's still rather safe on a personal machine.)
Mandriva currently lets you easily define which programs require the root password and which ones settle for the admin one - of course, you need the root password to do that! :p But other than that, overall, I prefer Ubuntu's default customisations than Mandrake/Mandriva's. I also prefer .deb packages to .rpm's.[/I]

Now, to run something as root, the command you'd usually use on Mandrake would be```
su -c *<command>*
```. This is basically the same as running ```
sudo *<command>*
```. HOWEVER, with su, you are always asked for the root password (not the admin's!)! With sudo, you are asked for your admin password.

So what's the difference between the root and admin passwords in such a case? The **/etc/sudoers** file. su does not care about this file, it is not even aware of its existence nor does it care for it. Now sudo uses this file, which "belongs" to it to grant the sudoer the priviledges determined by that file.
Here's an output from mine:
> # User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
Hence, the admin as the exact same priviledges that root does, but you can change that using **visudo**. Note: the above is from an unaltered /etc/sudoers file, hence a default Ubuntu setup.

In short, if your admin user(s) do(es) not have all rights as root does, you can still run a command as full-root by using su -c (or gksu -c or another equivalent) provided you give the root password.
Now to have a root password in Ubuntu, you'll have to manually set it up, as Ubuntu come out of the box withtou root-login permissions (hence, in general terms, you don't need a root password...).
On the other hand, setting a root password will in fact enable root login and I've read somewhere in the forum that the forum no longer permits such sharing of information as it goes against Ubuntu's security policies (I think I understand their point of view and to a point agree with it but I myself prefer to have things differently).
So, respecting the house rules, I will not share this here but if you want to, you can find information on the Intenet or I can give it to you privately (as I actually believe, besides the security resons, the greates advantage of Linux vs proprietary OS, in terms of developper/user trust, is **transparency**).


Finally, there is also a **difference** between **running something as root** and actually **working in a root environment** (as you'd login directly as root). In Mandrake/Mandriva, this is the difference between **su** and **su -**.
Running something as root means you run that something invoked as if by root.
Working in a root environment means the above + you have all the environmental variables of root (not the regular user that "pretends" to be root) and that e.g. .bashrc et al (if they exist) are executed from the root folder.

The above said, I myself never tried **sudo -i** but I easily believe it will attain the same objective as **su -**.

Regarding XFCE complaints, it's like someone said before, you are **running thunar as root but you are NOT root (for this latest you'd have to run from a root environment).** For thunar, the fact you are "running as" is dangerous enough (which it is!), hence the warning. ;)

Hope that helped. :)

---

### Post by HungryMan on 2008-12-15
@jdackle - give me a while to comprehend that, sudo being secure is kind of unclear to me because if anyone can do sudo, then what security is there in sudo if all you need is YOUR password, and not root's.

but I think it's clearer than a while ago. sudo = super user do, su= super user. the first just gives you admin rights in executing the command that follows sudo, and the last calls for the super user.

btw, if i get a root@computer-desktop:~#, does that mean i got root? I was able to get this twice under different circumstances already. Doing "cd ~" in one of the circumstances brought me to MY home directory, and not root's. I will try doing that on the other circumstance that gave me root@computer-desktop:~#. Note that I got ~# instead of /$, i thought /$ was for bash?

and thanks very much for helping me! i need this because i want to secure some (*nix) computers from unauthorized access.

---

### Post by HungryMan on 2008-12-15
ok, i think i've got root. because i got a terminal that says root@computer-desktop:/# and if i do a "cd ~" to it, I go to /root.

but the strange thing is, i did not even have to log-in to get root. I know Ubuntu disabled root by default, hence it doesn't have a password to begin with. I think I'm treading on dangerous waters here, but all I needed to get a root prompt was a simple "sudo XXXXXXXX XXX". I know this can simply be avoided by preventing access to the XXXXXXXX command.

Also, another curiosity. I tried "sudo rm -rf .Trashes" on OS X on a normal account, and as I said before, did absolutely nothing, not even complain that access is denied. Can I edit the sudoers file to allow me to "sudo rm -rf .Trashes" even on a normal account? Some people just delete their files in their USB Drives instead of shift-deleting, and OS X seems to be pissing about "Trash can not be moved to trash" or something like that.

One more, since most of those *nix systems will be OS X, root is more powerful than an administrator right? Because the OS X machines were set up with an administrator account and a student account, unfortunately, based off the security structure of Windows.

And one last question, does *nix have three user types (root, admin, normal) compared to Windows' two (admin and normal, or commonly called limited)?

---

### Post by jdackle on 2008-12-15
First off, you may have gotten me wrong... I am by no means an expert on Linux security or Linux alone. And for that matter, Linux is the only *nix I ever used in my life!
Also, I never administred any network, not even a private one, not even have I ever linked two computers together or shared an Internet or other service/device.
I am just someone who's been using Linux at home for some 7-8 years. And I'm curious. :mrgreen:

This said, I'll try and answer what I can:

> **HungryMan said:**
> @jdackle - give me a while to comprehend that, sudo being secure is kind of unclear to me because if anyone can do sudo, then what security is there in sudo if all you need is YOUR password, and not root's.
That was my issue exactly when I brought up the comparison with Mandrake/Mandriva.
HOWEVER, by default, Ubuntu makes the first user you create on your system an administrator with full privileges (via the sudo command). It then makes all users subsequently created UNprivileged users by default. 
[I](The basic assumption is: first user is created by the administrator so is logically the administrator itself. Subsequent administrators must be manually setup as such, otherwise they are setup as  unprivileged users by default.)
I am NOT talking root here! It comes "first" but I'll talk about it later.[/I]
Furthermore, with the /etc/sudoers you can grant different Administrator levels of privileges. You can thus have a top-Admin equal to root (to whom Ubuntu asks for authentication as the real person for specific sensitive tasks; otherwise, someone might someway use the top Admin account unlimitedly, this way it can only do trivial tasks, may accidentaly (or not) messup your personal documents and such but NOT the system itself).
You can then have a less privileged Admin level that can do some administration tasks but not others and still more levels - potentially in both vertical as horizontal different levels.
Hence, the password sudo asks you for is the password you need to be permited to perform a system-sensitive task you are defined, by /etcsudoers, fit to acomplish.
By default, the Top Administrator = First user created = root = has all unlimited privileges on the system. But that too can be changed, in the /etc/sudoers file. In this case, that should be done BEFORE handing the account over to the top Administrator of THAT account.
Hence, were you to prevent her/him from modifying the /etc/sudoers file, you would then be sure that admin, even though being the most privileged user on THAT computer-system would never actually be root (unless you, who setup the machine in the first place, changed that; NOTE that that would mean you could login to the machine as ROOT).
I think the above pretty much covers, in brief, the sudo + /etc/sudoers concept  of security.

> **HungryMan said:**
> but I think it's clearer than a while ago. sudo = super user do, su= super user. the first just gives you admin rights in executing the command that follows sudo, and the last calls for the super user.
Yep, that's pretty much it.
sudo is kind of a subset of su functionality BUT it does add something that su -c does NOT have: /etc/sudoers ;)

> **HungryMan said:**
> btw, if i get a root@computer-desktop:~#, does that mean i got root? I was able to get this twice under different circumstances already. Doing "cd ~" in one of the circumstances brought me to MY home directory, and not root's. I will try doing that on the other circumstance that gave me root@computer-desktop:~#. Note that I got ~# instead of /$, i thought /$ was for bash?
Answering the initial question: yes and no! :mrgreen: You are root in the sense you execute commands with root privileges. You are not root in the sense the environment is not root's.
Example:
```
su
``` gives me:> root@machine:/home/user# BUT
```
su -
``` gives me:> root@machine:~#
With su you *run as* root. With su - you *live* root's life!

> **HungryMan said:**
> and thanks very much for helping me! i need this because i want to secure some (*nix) computers from unauthorized access.
You're welcome. But you've been warned above! :mrgreen:

> **HungryMan said:**
> ok, i think i've got root. because i got a terminal that says root@computer-desktop:/# and if i do a "cd ~" to it, I go to /root.

but the strange thing is, i did not even have to log-in to get root. I know Ubuntu disabled root by default, hence it doesn't have a password to begin with. I think I'm treading on dangerous waters here, but all I needed to get a root prompt was a simple "sudo XXXXXXXX XXX". I know this can simply be avoided by preventing access to the XXXXXXXX command.
You did not necessarily "get root". In my example above, su (w/o the - parameter) does make /root your home directory but it is not the same as su - !

You've obfuscated the command you used (according to Ubuntu and this forum's policies, all great there) but that is NOT the way I myself know of for full-root. What I know about is **enabling the root account**. You'll then have to login as root.

> **HungryMan said:**
> Also, another curiosity. I tried "sudo rm -rf .Trashes" on OS X on a normal account, and as I said before, did absolutely nothing, not even complain that access is denied. Can I edit the sudoers file to allow me to "sudo rm -rf .Trashes" even on a normal account? Some people just delete their files in their USB Drives instead of shift-deleting, and OS X seems to be pissing about "Trash can not be moved to trash" or something like that.
I know nothing about OS X. Have used it but as kind of a "guest user" only.
Regarding the sudoers file, you should be able to do it, yes. For details: ```
man sudoers
```

> **HungryMan said:**
> One more, since most of those *nix systems will be OS X, root is more powerful than an administrator right? Because the OS X machines were set up with an administrator account and a student account, unfortunately, based off the security structure of Windows.
root, by default, is GOD! It can grant an Admin equal divinity. ;)
What happens on a Ubuntu system is that the Ubuntu team structured the system so as to root being kind of dorment - it's there but does not directly take initiative (unless you reconfigure your root account). root user numeric ID is always 0, the first user in the system, before all other system users and human users.
And still, the /etc/sudoers file allows to demote god itself! Ok, you have to be god to do that (or an admin raised to god level). I guess this might be useful in some kind of network where the machine where that root user is demoted is some kind of dumb-terminal or something.

> **HungryMan said:**
> And one last question, does *nix have three user types (root, admin, normal) compared to Windows' two (admin and normal, or commonly called limited)?
Regarding human users... yes and no! Regarding all kinds of users... yes and no! :mrgreen:
You have root - usually human but not always (in Ubuntu, root is never human out of the box, meaning you can not have root as the Windows Administrator and then a regular unprivileged user - but you CAN set it up that way).

But basically, human users:
root = Windows Administrator
other user = anything from totally unprivileged to totally privileged (= root) user. YOU define how privileged it is or not.
HOWEVER, in practical terms, in Ubuntu (and other GNU/Linux distros in general) you have root, first user = top admin and subsequent unprivileged users.
So in theory, no, you do not have three types of human users, only two or as many as different privilege levels you can come up with.
But in practice, it is sensible to think of three types of human users as you've described.

Then you have unhuman (no pun intended! :mrgreen:) users. These are such as daemon, bin, sys, etc. These are users which own specific executable files. Each of these users is allowed to perform specific tasks, thus allowing the corresponding commands (with SUID bit set) to be run with privileges by unprivileged users.
Ok, there is probably a lot more to system users than this but this is my personal understanding of it. Their numerical UIDs range, in Ubuntu, between 1 and 999 (in Mandrive, from 1 to 499). From 1000 upwards, human users. ;)

---

### Post by gTinker on 2008-12-15
[QUOTE=HungryMan]
One more, since most of those *nix systems will be OS X, root is more powerful than an administrator right? Because the OS X machines were set up with an administrator account and a student account, unfortunately, based off the security structure of Windows.[/quote]

This is really not the best place to ask questions about Apple operating systems. Even though they are similar to UNIX (or maybe BSD).

[QUOTE=HungryMan]
And one last question, does *nix have three user types (root, admin, normal) compared to Windows' two (admin and normal, or commonly called limited)?[/QUOTE]

No, GNU/Linux has as many user "types" (as you have used the word) as the admin has configured. There's 'root', 'admin' (a default on ubuntu because of the way Ubuntu structures sudo), some systems have a 'backup' group and there could be many other groups based on the normal administrative tasks the members of a group are authorised to carry out. 

[QUOTE=HungryMan]sudo being secure is kind of unclear to me because if anyone can do sudo, then what security is there in sudo if all you need is YOUR password, and not root's.[/quote]

That's the point, "everyone" can't do sudo on Ubuntu, the default is to make the user who installs the system to be in the admin group and with the ability to sudo, users added after install only get admin rights if expressly granted to them by the admin.

You can't really "get root" on Ubuntu, the default is that root can't logon, root has no password to guess or brute force. Sudo allows commands to be executed with root rights, it is not the same thing as being root (think environment). In addition, the ways you have been trying to defeat the setup can only be done by someone who is already given sudo rights. A limited user could not do that. 

It is possible to edit the sudoers file to allow all sorts of stupid things to be possible, that's why only a qualified admin should muck around in there.

Never forget, while you are securing these systems you mention, that physical access to the console of a system means it can be compromised, Windows, Mac, Ubuntu GNU/Linux.

---

### Post by HungryMan on 2008-12-16
thanks for all the responses guys!

i guess the only sure way to clear the whole confusion i have is to try it first hand. :D

@jdackle - I think I google can help me in case I want/need to enable root in ubuntu. Thanks for the help! :)

---

### Post by jdackle on 2008-12-16
Glad we could help. :)

Just one more thing: you can override all system permissions IF you boot your machine in RESCUE MODE. In that case, you are basically root and you are asked NO password for that.
Solutions:
A) Disable Rescue mode boot option in GRUB (or whatever bootloader you may be using)
B) Password-protect Rescue mode. GRUB can do that. You can also use startup manager for a GUI to set this one up:```
sudo apt-get install startupmanager
```

For A), you can install qgrubeditor for a GUI:```
sudo apt-get install qgrubeditor
```. It allows for GRUB password setup as well but I couldn't find an option specific to rescue-mode.

---

### Post by HungryMan on 2008-12-16
i'll remember that. :)

and is it safe to say such things? i don't want to be the reason why you'll be banned or suspended.
just concerned.

---

### Post by jdackle on 2008-12-16
lol
Erm, I didn't actually think of that... But it's basically just a warning about a potential security flaw (not quite in Ubuntu, rather in your (non) configuration).

The "don't disclose how to enable root account" policy of Ubuntu is somewhat different, I believe. I think it's meant to prevent the uncautious newbie from using the root account as a normal account - i.e. were the root account enabled by default, the uncautious newbie might get used to use that one *instead* of the regular one, i.e. the user running the root account as if it were a normal (first Ubuntu user) account might not even be aware of whether or not he/she was performing a system administrative task as no authentication would be asked of him/her to perform them (he/she would already be logged in as root). That and the actual real point: opening your user-account to the outside is sometimes useful, it's simply dangerous to do it logged in as root...
In other words, it's a sort of "pedagogical" security-policy + protecting the user from himself/herself...

Mind you this is just my opinion on this Ubuntu's policy. And for a few years on this forum you could freely share the knowledge about enabling the root account on your system.

Ubuntu has made quite an entrance in the Linux world. There were plenty "easy", "user-friendly" distros out there before already. But the way you can see Ms.Windows mainly based sites talk of Ubuntu nowadays... I mean... they talk "Ubuntu" more than they talk "Linux"... That I do not remember seeing before. 
I do believe Ubuntu's greatest asset was to make the bridge to the Ms Windows user **mindset**. And that **beyond the appearence level**.

I mean, Mandrake, considered by many the most user-friendly distro befor Ubuntu, prefered KDE over GNOME, being the former more "like-Windows" than the later. Mandriva now packs restricted/proprietary software (drivers, flash plugin, ...) with their installation CDs! The Penguin Liberation Front, one of the first restricted/proprietary-software repos, was directly aimed at providing packages for Mandrake (only later to other distros).

If you closely look at it, Mandrake/Mandriva is more "like Windows" on the surface. But Ubuntu managed to become more widely accepted by the public by means such as "removing" the root account from the system. 
Additionaly, separating the open source software from the restricted/proprietary software in a way that forces the user to take the initiative to search for the proprietary software, being less user-friendly than say Mandriva's aproach, raises the user awareness about the difference - the user learns an extremely important point abouth GNU/Linux.

Ironically, IMHO, the key for Ubuntu's success is that it prevents the user from immediately accessing the full power of Linux! And THIS CAN BE AN ADVANTAGE!
For one, if you were a power-user in Windows, you are used to search deep for the knowledge to be so. If you never were, you're safer with restricted power on Ubuntu than on potentially other distros.
In older distros, the user would be handed full power with very little effort AND very little education. That meant the user might quite easily break his/her Linux system and then blame it on Linux.
With Ubuntu, you are lead to being more educated about what you are doing - hence, you break your system less and when you do do it, you are more aware of your own faults. It increases the pleasure of learning by making it *safer to "learn by mistake"*. **It's not the Ubuntu distro that is safer, it's the Ubuntu user that is *better* (not "more") educated**.

Again, [COLOR="DarkRed"]these are just my thoughts! I have read this NOWHERE, they are NOT AFAIK a portrait of Ubuntu's official position. I DO NOT KNOW what that position is as I never actually tried to find it out![/COLOR]
I did notice the warning regarding the information on enabling the root account and have tried and been respectful to it.


Regarding the GRUB password protection, I think it quite different. It's a quite basic security measure to prevent your system from being compromised by third parties (again, password-protecting the recovery mode might prevent the average user from using that feature, were she/he to forget the seldomly-used said password...).
Hence my warning and my tip.


Sincere thanks for your concern, HungryMan. :)

---

### Post by gTinker on 2008-12-17
HungryMan,
My recommendation is to use your admin account (the first one configured when you install, which has sudo rights) to configure your system but to add another limited user(s) (without sudo rights) for day-to-day computing tasks, that protects the user(s) from themselves and even if someone compromises the user, they don't get to sudo, so your system is preserved. It would be bad enough losing your user, but worse losing your whole system.


[QUOTE=jdackle]
Regarding the GRUB password protection, I think it quite different. It's a quite basic security measure to prevent your system from being compromised by third parties (again, password-protecting the recovery mode might prevent the average user from using that feature, were she/he to forget the seldomly-used said password...).
Hence my warning and my tip.[/QUOTE]

I believe this is worthwhile for the casual passerby, however, anyone who can boot a live CD on your system can be considered 'in". In addition, I think you should hide or remove the Rescue Mode or the whole GRUB menu, unless these systems you are setting up require the users to multi-boot for some reason. For data security in an enterprise situation you probably should consider encryption.

---

### Post by jdackle on 2008-12-17
> **gTinker said:**
> I believe this is worthwhile for the casual passerby, however, anyone who can boot a live CD on your system can be considered 'in". In addition, I think you should hide or remove the Rescue Mode or the whole GRUB menu, unless these systems you are setting up require the users to multi-boot for some reason. For data security in an enterprise situation you probably should consider encryption.
Yes, live CD (as well as another installed bootable distro or even Windows with the ext2-fs driver (don't know about OS-X but wouldn't be surprised it can read/write from/to an ext2 or ext3 partition (assuming you are using one of these fs types))) can get you in just as well as you were logged in as root from within your system. I should have mentioned that...
However, I do believe that to make changes to the /etc/sudoers file you'll actually need to run visudo from within your system session. But I am just guessing here. Of course, in any case, most everything else is doable from e.g. a Live CD. 
I kind of assumed that as obvious and, security against that being needed, you'd make the apropriate changes to the machine's BIOS setup and password-protect that same BIOS.

Still regarding GRUB, you should not only password-protect the recovery mode (should you choose to keep it) but the builtin GRUB command-line execution too. Otherwise, any knowlegeable user can boot whatever he/she wants to...

---

### Post by gTinker on 2008-12-18
[QUOTE=jdackle]
However, I do believe that to make changes to the /etc/sudoers file you'll actually need to run visudo from within your system session. But I am just guessing here. [/QUOTE]

Naw, you could edit that file with any other editor too, even a GUI.

If nothing else, with a bootable CD, you could mount the filesystem at some mountpoint and chroot into it and then do whatever you liked, for instance, add yourself as an admin user.

But we are getting far afield of the OPs question, the systems he is setting up are probably not going to be ones that require airtight security, likely just a simple workgroup, otherwise, it would be being done by someone who wouldn't have to ask the question.

---

### Post by pietjanjaap on 2008-12-18
Remember that in 1 minute you can change the admin password, same for windows, that is if you have the pc within reach.

---

### Post by HungryMan on 2008-12-18
@gTinker - yeah, I don't really need airtight security, just need the assurance that someone can't just do whatever he likes with the computers at school. I'm not really going against 1337 h4xxorz, just plain old people who might even think that CLI is sooo 1970's. But I don't want to take any chances. Also, I'm doing this out of my own free will, not because I was forced to do so.

@pietjanjaap - if i remember correctly, it's "net <username> <password>", and that you need to have admin rights. I loved that. XD
When people spy on my keystrokes and change my password, I use that. They'll just go like: "How the hell did you guess the password I put there!?"

---

### Post by jdackle on 2008-12-18
> **gTinker said:**
> Naw, you could edit that file with any other editor too, even a GUI.
Yes, I know you can edit it with any text-editor provided you have write-access to it. I was just wondering would the changes actually take effect if they were done with some editor other than visudo...

> **gTinker said:**
> If nothing else, with a bootable CD, you could mount the filesystem at some mountpoint and chroot into it and then do whatever you liked, for instance, add yourself as an admin user.
Well, yes, I didn't think of that. That would allow you to run the mounted filesystem's visudo anyways...
I guess the BIOS configuration would be mandatory then. "Even" old people can slip in a Live CD and eventually follow some online instructions (there are some that include the sudoers file to e.g. displaying the firestarter icon without the need for a password...).

> **HungryMan said:**
> @pietjanjaap - if i remember correctly, it's "net <username> <password>", and that you need to have admin rights. I loved that. XD
When people spy on my keystrokes and change my password, I use that. They'll just go like: "How the hell did you guess the password I put there!?"
I wonder if sharing THAT would be against Ubuntu's policies... :mrgreen:

---

### Post by HungryMan on 2008-12-19
> **jdackle said:**
> Yes, I know you can edit it with any text-editor provided you have write-access to it. I was just wondering would the changes actually take effect if they were done with some editor other than visudo...

...

I wonder if sharing THAT would be against Ubuntu's policies... :mrgreen:

I think visudo justs make sure that you don't enter anything wrong. Based off what I was reading, it's just vi with strict syntax and grammar checking. It also said that sudo won't run at all even for just a minor mistype.

LOL. I don't think they'll mind me sharing net user. oh... and i think it's "net user <username> <password>"

---

### Post by gTinker on 2008-12-19
[QUOTE=jdackle]Well, yes, I didn't think of that. That would allow you to run the mounted filesystem's visudo anyways...
I guess the BIOS configuration would be mandatory then. "Even" old people can slip in a Live CD and eventually follow some online instructions ...
[/quote]

Well, being an "old people" myself, I can attest to the fact that we can load a live CD. In addition, unless you put a lock on the case that doesn't allow us in, we could also reset the BIOS PROM back to default, no password. However, for HungryMan's systems, I agree the BIOS should be passworded to keep his students out. I would disable CD or USB booting too, in case some students are more clever than expected.

[edit] And, if any of these systems has a floppy drive, booting from it should be disabled too or else some student with Smart Boot Manager on floppy will use it to boot a CD.

---

### Post by jdackle on 2008-12-19
> **gTinker said:**
> Well, being an "old people" myself, I can attest to the fact that we can load a live CD. In addition, unless you put a lock on the case that doesn't allow us in, we could also reset the BIOS PROM back to default, no password. However, for HungryMan's systems, I agree the BIOS should be passworded to keep his students out. I would disable CD or USB booting too, in case some students are more clever than expected.

[edit] And, if any of these systems has a floppy drive, booting from it should be disabled too or else some student with Smart Boot Manager on floppy will use it to boot a CD.

lol, yes, "old people" (I wonder if 32 can fit in that term for some ... :lol: ) can be very annoyingly knowlegeable and able ... :mrgreen:

Regarding the disabling of CD, USB, floppy booting, that was what I meant with "appropriate changes to the BIOS ... and then password-protect the BIOS setup" so that booting from those devices cannot be re-enabled. Actually, in principle, booting from any device other than the one where the OS to be used is mounted should be disabled. Case arising that the admin (HungryMan in this case) would need to boot from another device, he could then just use his password to enter the BIOS setup and enable that.

---

### Post by gTinker on 2008-12-19
[QUOTE=jdackle]lol, yes, "old people" (I wonder if 32 can fit in that term for some ... :lol: ) ..[/quote]

Perhaps it could, I know when I was in my 20s, we used to say, "don't trust anyone over 30". But, that was 40 years ago.

---

### Post by jdackle on 2008-12-27
> **gTinker said:**
> Perhaps it could, I know when I was in my 20s, we used to say, "don't trust anyone over 30". But, that was 40 years ago.:)

---

