---
title: "Grub 2 Password Protection"
date: 2009-12-31
forum: Tutorials
---

### Post by drs305 on 2009-12-31
This page has been migrated to the Ubuntu Community Documentation site. For the most up-to-date information, please visit:
[https://help.ubuntu.com/community/Grub2/Passwords]("https://help.ubuntu.com/community/Grub2/Passwords")

The above page is a sub-page of the main community documentation regarding [https://help.community/Grub2/]("https://help.ubuntu.com/community/Grub2").

Thank you to all the users who posted in these threads and expanded our knowledge of Grub 2 since it's introduction.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12073029](http://ubuntuforums.org/showthread.php?p=12073029)


Support threads regarding the wiki and it's content should be created in a suitable forum.

------

[COLOR=MAROON][B][SIZE=4][CENTER]*Grub 2 Password Protection*
[/CENTER]
[/SIZE][/B][/COLOR] 
[B][COLOR=Navy]
[LIST=1]
[*]Introduction
[*]How It Works
[*][COLOR="DarkRed"]Warnings & Cautions[/COLOR]
[*]Setup
[*]Protecting All Menu Items
[*]Examples (PW Protect Windows Recovery)
[*]Password Encryption - *grub-mkpasswd-pbkdf2*
[*]Internal Links
[*]External Links
[/LIST]
[/COLOR][/B]
[LIST=1]

[*]**[COLOR=Navy][SIZE=3]Introduction to Grub 2 Basic Password Protection[/SIZE][/COLOR] **
Password protection in Grub 2 is still being developed and its behavior may change in future updates. In this guide, when the term "Grub 2" is used it refers to the version of Grub 2 (grub-pc) available in the *main* Ubuntu repository. Any time Grub 2 is updated, the user should note whether their password protection is still working as expected.
[COLOR="DarkRed"]**These instructions are primarily for 1.98**[/COLOR]. Advanced capabilities such as encrypted passwords which have been introduced in Grub 1.98 are still being worked on. Some of the advancements work well while others do not. 

[LIST]
[*]This is basic password security. The username/password are unencrypted; anyone having physical access to the machine and more than an elementary knowledge of how Linux works will be able to access the configuration files and bypass this feature. Encrypted password protection is on the horizon and available in an experimental version of Grub 2 (see "The Future" section below).
[*]Grub 2 can set password protection on specific menuentries and for specific users. For example, "John" can access Ubuntu but not the Windows recovery mode, which is only accessible by "Bill", the superuser.
[*]Automatic password protection has not yet been automated. Menuentries must be identified manually by editing the Grub 2 */etc/grub.d/* scripts such as 10_linux and 30_os-prober.
[*]If password protection is enabled, even if for only one entry, and even if not for the *superuser*, the superuser name and password are required to gain access to the Grub 2 command line and menu-editing modes.
[*]The username and/or password do not have to be the same as the Ubuntu logon name/password.
[/LIST]


[*]**[COLOR=Navy][SIZE=3]How It Works[/SIZE][/COLOR]**
[LIST]
[*] To enable basic password protection, the user/administrator must add a *superuser* (and other users if desired) and password(s)  to the */etc/grub.d/00_header** file and manually designate which menuentries require a password in the */etc/grub.d/* files. 

[*]The Grub 2 menu can include both password-protected and non-protected entries.
[*]Once the password feature is enabled the Grub 2 menu will appear as it does normally. When a selection requiring a password is required, the user will be prompted to enter the correct username and password. If entered correctly, the selected menuentry will continue to boot. If incorrect, the user will be returned to the Grub 2 menu.
[*] If Grub 2 is set up to boot directly to a password-protected menuentry without displaying a menu, the username/password prompt will appear and booting will not occur until they are correctly entered. 
[*]Here is a sample menu with passwords enabled, provided by one of the Grub 2 developers:
> 
set superusers="user1"
password user1 password1
password user2 password2

menuentry "GNU/Linux" {
        set root=(hd0,1)
        linux /vmlinuz
}

menuentry "Windows" --users user2 {
        set root=(hd0,2)
        chainloader +1
}

[LIST]
[*]*user1* is the designated *superuser*. This user can boot any menuentry, edit items in the Grub 2 menu during boot, and use the Grub 2 command line.
[*]Anyone can boot GNU/Linux
[*]Only *user2* and the *superuser* can boot Windows in this example.
[/LIST]
[*]* Technically, the *superuser/user* information and password do not have to be contained in the */etc/grub.d/00_header* file. The information can be placed in any */etc/grub.d* file as long as that file is incorporated into *grub.cfg*. The user may prefer to enter this data into a custom file, such as */etc/grub.d/40_custom* so it is not overwritten should the Grub package be updated. If placing the information in a custom file, do *not* include the "cat << EOF" and "EOF" lines as the content is automatically added from these files.
[/LIST]


[*]**[COLOR=DarkRed][SIZE=3]Warnings & Cautions[/SIZE][/COLOR] **

[LIST]
[*][COLOR=DarkRed]Errors in creating a password-protected Grub 2 menu may result in an unbootable system. To restore a system with broken passwords, access and edit the Grub 2 configuration files using the LiveCD or another OS.[/COLOR]

[*]If password protection is enabled, only the designated superuser can edit a Grub 2 menu item by pressing "e" or use the command line by pressing "c".

[*][COLOR=Red]Caution:[/COLOR] If Grub 2 is set up to boot automatically to a password-protected menuentry the user has no option to back out of the password prompt to select another menuentry. Holding the SHIFT key will not display the menu in this case. The user must enter the correct username and password. If unable, the configuration files will have to be edited via the LiveCD or other means to fix the problem. 

[/LIST]


[*]**[COLOR=Navy][SIZE=3]Setting Up Password Protection[/SIZE][/COLOR] **
There are three steps to enabling Grub 2 password protection. The user must set up the authorized users, designate the password(s), and identify the password-protected menuentries in the */etc/grub.d/* scripts.


[LIST=A]
[*][SIZE="2"]**Superuser & Password Designation** (Required)[/SIZE]
A superuser must be designated. This superuser can access any menuentry, edit the menuentries in the Grub 2 menu by pressing "e", or invoke the Grub 2 command line mode.


[LIST]
[*]Add the following the bottom of */etc/grub.d/00_header*
>  
cat << EOF
set superusers="user1"
password user1 password1
EOF

Example: 
>  
cat << EOF
set superusers="superman"
password superman 1234
EOF

[/LIST]


[*][SIZE="2"]**Other Users** (Optional)[/SIZE]
Other users can be identified and given a password. A designated user can access unprotected and his/her own menuentries. 


[LIST]
[*]Add the following the bottom of */etc/grub.d/00_header*
>  
cat << EOF
set superusers="user1"
password user1 password1
password user2 password2
EOF

Example: 
>  
cat << EOF
set superusers="superman"
password superman 1234
password bill 5678
EOF

[/LIST]


[*][SIZE="2"]**Designating Menuentries for Password Protection**[/SIZE]
Once the superuser/other users and their password(s) are established, the entries to be protected must be identified. Currently Grub 2 adds no password protection to any entries upon establishment of a superuser and password in */etc/grub.d/00_header*. (Note: This may change. See "The Future" section below.) Each menuentry must be identified and modified.

Scripts can be used to tailor entries for specific menuentries. See the "Scripts" section for examples. The remainder of this section will explain how to change the main script files in */etc/grub.d/* to set up password protection for entire classes of menuentries (Linux on the main partition, OSs on other partitions, memtest86+, etc). Remember that editing the */boot/grub/grub.cfg* file directly is discouraged.

For protecting specific menuentries, another option is to add entries to the */etc/grub.d/40_custom* file and disable the applicable script file in the same folder. For example, copy the Windows entries from */boot/grub/grub.cfg* to 40_custom, add "--users user1" to the desired entry (such as the Windows recovery partition) and then remove the executable bit from */etc/grub.d/30_os-prober*.


[LIST]
[*]**Password protect all Linux kernels on the main partition**: **[COLOR="DarkGreen"]*/etc/grub.d/10_linux*[/COLOR]**:

From newer Grub2 versions (1.98-1ubuntu5)(approximately line 74):
> printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}" { 
To allow the *superuser*  only:
> 
printf "menuentry --users *user1* '${title}' ${CLASS} {\n" "${os}" "${version}" { 

Example to permit access by only the *superuser* (superman):
> 
printf "menuentry --users *superman* '${title}' ${CLASS} {\n" "${os}" "${version}" { 

Example to permit access by the *superuser* (superman) and *bill* (Note, for multiple users, separate the names with a comma - *bill,john,jill*):
> 
printf "menuentry --users *bill* '${title}' ${CLASS} {\n" "${os}" "${version}" { 


From older Grub2 versions (approximately line 59):
> menuentry "$1" { To allow the *superuser*  only:
> 
menuentry "$1" --users user1 {

Example to permit access by only the *superuser* (superman):
> 
menuentry "$1" --users *superman* {

Example to permit access by the *superuser* (superman) and *bill*:
> 
menuentry "$1" --users bill {

[/LIST]



[LIST]
[*]**Password protect the *Recovery Mode* option**: [COLOR="DarkGreen"]*/etc/grub.d/10_linux*[/COLOR]  Also make the change as described in the */etc/grub.d/00_header* section above. 
For GNU GRUB 1.98-1ubuntu12. change this section to the following (add the user information and include the 'printf' line inside each conditional rather than following them:
> if ${recovery} ; then
title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
printf "menuentry '${title}' ${CLASS} --users drs305 {\n" "${os}" "${version}"
else
title="$(gettext_quoted "%s, with Linux %s")"
printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
fi 


From (GNU GRUB 1.98-1ubuntu5):
> 
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"


To:
> 
if ${recovery} ; then
  printf "menuentry '${title}' --users *user1* ${CLASS} {\n" "${os}" "${version}"
else
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
fi

[/LIST]

[LIST]
[*]**Password protect the *memtest86+* option**: [COLOR="DarkGreen"]*/etc/grub.d/20_memtest*[/COLOR][/B] . Also make the change as described in the */etc/grub.d/00_header* section above. 
> 
menuentry "Memory test (memtest86+)" --users *superman* {
Additional *memtest86+* entries (from other partitions) may also be located in this file. The line will start with "*menuentry*". Change these lines as desired.
[/LIST]


[LIST]
[*]**Password protect kernels/operating systems on other partitions**: [COLOR="DarkGreen"]***/etc/grub.d/30_os-prober***[/COLOR]. Also make the change(s) as described in the */etc/grub.d/00_header* section above. 

Linux entries on other partitions:
> menuentry "${LLABEL} (on ${DEVICE})"  --users *superman* {
Other Operating Systems, including Windows:
> 
menuentry "${LONGNAME} (on ${DEVICE})" --users *superman* {

OSX entries (in the *macosx)* section:
> 
menuentry "${LONGNAME} (on ${DEVICE})" --users *superman* {

[/LIST]
Save the files, run "sudo update-grub", and reboot.
[/LIST]


[*]**[COLOR=Navy][SIZE=3]Protecting All Entries[/SIZE][/COLOR]**
Grub 2 password protection is still evolving. Currently password protection must be assigned to each menuentry. Protecting the entire menu *from editing* can be accomplished by adding the *superuser* and password without designating a specific menuentry. 

For now, there is no automatic method in Grub 2 to password-protect every menu item. At some point it is expected that this feature will be incorporated in grub-mkconfig. For now this can be accomplished by running the following command(s). 

[COLOR="DarkRed"]Before rebooting make sure you have added the "superuser" and password to *etc/grub.d/00_header* and inspect */boot/grub/grub.cfg* to ensure you achieved the desired results. [/COLOR]

Notes: 
[LIST]
[*]The way Grub 2 assigns password protection may change. Currently the default is for menuentries to be *unlocked*. The developers are considering making the passwords mandatory for all entries once a superuser is designated. The superuser would then be able to *unlock* entries. If this feature is incorporated in the Ubuntu version of Grub 2 I will update these instructions. 
[*]The first two ccommands make backups of the files to be modified.
[*]*filename(s)* should be replaced by the specific script file names you wish to change. These files are located in */etc/grub.d/* and include *10_linux, 20_memtest86+, and 30_os-prober*. You can include one or more in the commands.
[/LIST]

```

sudo mkdir /etc/grub.d.backup
sudo cp /etc/grub.d/* /etc/grub.d.backup
sudo sed -i -e '/^menuentry /s/ {/ **--users user1** {/' *filename(s)*

```Example:
```

sudo sed -i -e '/^menuentry /s/ {/ --users *superman* {/' */etc/grub.d/10_linux  /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober /etc/grub.d/40_custom*

```To undo the previous command, run:
```

sudo sed -i -e '/^menuentry /s/ --users ***[COLOR="DarkRed"]user1[/COLOR]*** {/ {/' *[COLOR="DarkRed"]filename(s)[/COLOR]*

```
Example:
```

sudo sed -i -e '/^menuentry /s/ --users *superman*[/B] {/ {/' *[COLOR="DarkRed"][I]/etc/grub.d/10_linux  /etc/grub.d/20_memtest86+ /etc/grub.d/30_os-prober /etc/grub.d/40_custom*[/COLOR][/I]

```
Save the files, run "sudo update-grub", and reboot. At the Grub 2 menu, you will be presented with the normal menu. When you make a selection, a prompt will ask for the username and password. 


[*]**[COLOR=Navy][SIZE=3]Examples[/SIZE][/COLOR]**


[LIST]
[*][SIZE="2"]**Password Protect the Windows Recovery Partition**[/SIZE]

Note: See the [Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") thread if you want to remove the Windows Recovery option from the menu entirely.

[LIST=1]
[*]Determine the Windows Recovery partition (sda1, sda2, etc).
[*]Add the desired username and password as described in Section 4A and 4B to */etc/grub.d/00_header*.
[*]Open */etc/grub.d/30_os-prober* for editing:
```

cd /etc/grub.d/
sudo cp 30_os-prober 30_os-prober.bak # Make a backup copy
sudo chmod -x 30_os-prober.bak        # Remove executable bit
gksu gedit 30_os-prober &

```
Change the following (approximately line 100)
From:
> 
[COLOR="Navy"]      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF[/COLOR]

To:
> 
[COLOR="DarkRed"]if [ ${DEVICE} = "/dev/sd[COLOR="Red"]XY[/COLOR]" ]; then
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" [COLOR="Red"]--users user1[/COLOR] {
EOF
else[/COLOR]
[COLOR="Navy"]      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF[/COLOR]
[COLOR="DarkRed"]fi[/COLOR]

Example setting protection on sda2 for user *superman*:
> 
if [ ${DEVICE} = "/dev/sd[COLOR="Red"]a2[/COLOR]" ]; then
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" [COLOR="Red"]--users *superman*[/COLOR] {
EOF
else
      cat << EOF
menuentry "${LONGNAME} (on ${DEVICE})" {
EOF
fi



[*]Save the file, then run:
```
sudo update-grub

```
You can use the same concept on other menuentries. Rather than using the partition designation {DEVICE}, you could use other unique identifying variables, such as . The title variable depends on the operating system. Examples include {LONGNAME} or {LLABEL}. 

My thread on [Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") may give you some ideas of how to alter the basic scripts to suit your needs.

[/LIST]
[/LIST]


[*]**[COLOR=Navy][SIZE=3]Password Encryption - *grub-mkpasswd-pbkdf2*[/SIZE][/COLOR]**

Although Grub 2 encrypted password protection has been available in all versions of Grub 2, it was initially a bit buggy. Forum member *georgemc* in Post #35 reported that it was working in Grub 1.99 (Natty) and my subsequent tests confirm his findings.

One of the drawbacks of the password set up discussed so far is that the passwords are entered in plain text in the Grub 2 files. While physical access to the computer cannot prevent access, the measure of security can be greatly enhanced by using Grub 2's *grub-mkpasswd-pbkdf2* command. This command converts your desired password into a very long alphanumeric code which is placed in the Grub 2 files. Your actual password is no longer visible in the Grub 2 scripts.

[COLOR="Red"]Note:[/COLOR] If you are going to experiment with encrypted passwords, make sure you have at least one good non-password protected menuentry to boot or you may not be able to log on if you encounter problems. 


[LIST]
[*]To generate an encrypted password, open a terminal and run the following command:
[LIST]
[*]```
grub-mkpasswd-pbkdf2
```
[LIST]
[*]Enter the desired password, the reenter it when prompted.
[*]Copy the resulting code. In a terminal, highlight the code and CTRL-SHIFT-c to place it in memory. 
[*]Paste the code after the username(s). Pasting can be accomplished in a text editor by either CTRL-v or middle mouse click.
[*]Example (shortened for formatting purposes):  
[*]> password_pbkdf2 drs305 grub.pbkdf2.sha512.10000.71C5B50F5ECB0EE953AB185684FABAC
[/LIST]


[*]The format for an encrypted password entry in /etc/grub.d/00_header would look similar to:
[LIST][*]> 
set superusers="drs305"
password_pbkdf2 drs305 <some really long alphanumeric entry generated from the grub-mkpasswd-pbkdf2 command>

[/LIST]
[/LIST]
[/LIST]


[*]**[COLOR=Navy][SIZE=3]Internal Links by the Author[/SIZE][/COLOR] **
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") 
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[Grub 2 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")


[*]**[COLOR=Navy][SIZE=3]External Links[/SIZE][/COLOR] **
[Grub Wiki:Authentication]("http://grub.enbug.org/Authentication")
[Felix Ziecle's Experimental Grub PPA]("https://launchpad.net/~fzielcke/+archive/grub-ppa")
[Grub 2 Community Doc]("https://help.ubuntu.com/community/Grub2")
[/LIST]

---

### Post by supertails on 2010-01-07
What if you have an older grub?

---

### Post by drs305 on 2010-01-07
> **supertails said:**
> What if you have an older grub?

I would prefer to keep this thread about Grub 2 but should probably have included a link for Grub Legacy users. For those seeking the answer to the same question, here is a link concerning Grub and password protection:
[ HOWTO: Password protect your GRUB entries  ]("http://ubuntuforums.org/showthread.php?t=7353")

---

### Post by ranch hand on 2010-01-30
In section 2 you have;
> 
To enable basic password protection, the user/administrator must add a *superuser*  (and other users if desired) and password(s)  to the */etc/default/00_header*  file and manually designate which menuentries require a password in the  */etc/grub.d/* files.

What */etc/default/00_header*  file?  I have grub1.96 on PhatDebian and 9.04, grub1.97beta4 on some 9.10 versions (3) and grub1.98 on all 10.04 installs.  None of these has a */etc/default/00_header*  file.  

Am I missing some thing or is that a typo?

I have  a System76 laptop coming for my Silversmith wife and want a little more protection as she will be taking it to shows.  This means that I am playing with this now to figure out how to set her box up.

I am going to try this with one of my 9.10 respins assuming it is a typo.

---

### Post by ranch hand on 2010-01-30
Well, that is slicker than grass through a goose.

Created a superuser and a second user.  Require superuser for Zenix and second user for Stone Edition1.2.

Log in with superuser was great on both and second user had no trouble logging in to Stoner.  Left the others "open".

Switched grub back to this OS and booted to Zenix login with no trouble so I can forget I did that and be cool (people wonder why I have so many OS' on my test drive).

I really love the ease of switching the boot/root from one OS to another in grub2.  What a great boot loader it is.

---

### Post by drs305 on 2010-01-31
> **ranch hand said:**
> In section 2 you have;

What */etc/default/00_header*  file?  I have grub1.96 on PhatDebian and 9.04, grub1.97beta4 on some 9.10 versions (3) and grub1.98 on all 10.04 installs.  None of these has a */etc/default/00_header*  file. .

It's /etc/grub.d/00_header.  It's referenced that way in all but the general overview. I've corrected it.

---

### Post by ranch hand on 2010-02-12
I bought a System 76 laptop for my wife with 9.10 installed.   We had a little problem with grub1.97beta4 and it now is running grub1.98.

In 1.97beta4 the password protection did work fine.

Trying it in 1.98 turned out to be a bad mistake.  The username prompt comes up and looks right but there is a cursor prompt like flasher double spaced below it and you can't enter a name.  Hitting enter gives you the password prompt with the same thing.

It was exciting because, like an idiot, I had protected all entries.

For now anyway, in case some one is thinking about trying this in grub1.98, I would not do it.  If you do, at least be smart enough to leave an unprotected one until you have tested real well.  It wastes a lot of time fixing stupid mistakes.

---

### Post by drs305 on 2010-02-12
Thanks for the report *ranch hand*. I mention in the original post that this guide is for 1.97~beta, which is the standard for Karmic. Several times I thought I could update it for 1.98 for Lucid but my results have been mixed and decided not to. However, I can and will add a note that the instructions are only for 1.97~beta for now.

---

### Post by ranch hand on 2010-02-12
Yes, that is probably a good idea.

I did read that and took note of it too.  Little things like that do not stop me from trying it though.

I should be smart enough, particularly on the wifes box, to do these things with care.  I sure wasn't that time.

What is really silly is that there is a boot password option in bios that I really should try.  I can get back to that to change it easier.  Yes, I do have a password to access the bios.

She will be taking this to shows (Silversmith) and I would like some security on the bugger.  It is pretty good right now unless someone trying to get in is a Linux user.

---

### Post by drs305 on 2010-02-26
I am looking for feedback on password protection in Lucid A3. I am currently not able to get password protection to work in A3. (Latest grub build 1.98~20100128-1ubuntu3).

I can generate passwords with "grub-mkpasswd-pbkdf2".
I can import the passwords from 00_header into grub.cfg as normal.

With either encrypted or unencrypted passwords in Lucid, the Grub menu hangs and does not respond most of the time. When I *can* get to the username/password entries, it allows me enter a username (after a lengthy delay) but reverts to the menu as I type the password.

If anyone is successfully using passwords in Grub 2 with Lucid, please say which version you are using and if you had to do anything special to get it working.

---

### Post by ranch hand on 2010-02-26
I am glad to hear that it isn't just me.

Am fighting with several other things in 10.04 but will be getting back to this in a couple of weeks.

---

### Post by drs305 on 2010-02-26
Update:
I just tried enabling the *console* mode in /etc/default/grub and in console mode both encrypted and unencrypted password/authentication works as it should. Of course, in this mode backgrounds will not be available.
> GRUB_TERMINAL=console

---

### Post by ranch hand on 2010-02-26
Wow, I was going to try that and was too chicken at the time.  That is great.

I will give it a whack one of these days on one of these installs on my box.  If it works I will just slap that on the wifes.

No background!!  Oh My What Will We Do?

Security or Background?  That is a tough one.

My main use of backgrounds is to use the wallpaper from the install supplying grub at the time so I know at a glance which I am using.  I bet if I have one with a black background I can tell it too.

The Wifes background is very nice but you don't see it for very long.  I think she will get over it and she only needs that security when away anyway.  Two sets of the needed files and we are all set.  One secure and the other not so secure.

Thanks a bunch.

---

### Post by drs305 on 2010-02-26
> **ranch hand said:**
> Wow, I was going to try that and was too chicken at the time.  That is great.
Thanks a bunch.

I was pleasantly surprised that it worked, even with the encrypted password using grub-mkpasswd_pbkdf2. 

I should note the encrypted passwords are available in Grub 1.98+ (Lucid) or the experimental branches, not in Karmic and 1.97~beta.

@ ranch hand:  I'm off for a week, so I expect you to have everything Grub 2-related solved by the time I get back.  ;-)


**[COLOR="Red"]Caution Added:[/COLOR]** In playing a bit with this, I found that encrypted function still isn't working as it should. When trying to get into the *edit* mode I get the username and p/w prompts, but then it takes me back to the main menu.  Without editing capability, *make sure you have at least one entry you know will work, otherwise you won't be able to try to recover a boot via command line or editing*.

Update 3/8/2010: With build 1.98~20100128-1ubuntu4 the encrypted passwords are working fine if I have *GRUB_GFXMODE=console * as the option in /etc/default/grub. When attempting to use it in *gfxterm* mode the password mode still seems to hang.

---

### Post by ranch hand on 2010-02-27
While my wifes box does run 9.10, it also is running grub1.98.  I have access to the 10.04 repo.

I have a sources.list.lizard (10.04 is called Lounge Lizard isn't it) that just has the main lucid repo on it.

Change the name of the real sources list to sources.list.kinky (9.10+Kinky Kitty) and drop the .lizard and you can have the newest kernel and grub if you want them. 

Kinky runs real well on 2.6.32 by the way.  My wifes just runs on 31.  I just want it stable.  It will get upgraded to the Lizard when System76 says it will work with their drivers.  I may try them before that but not on hers.

EDIT
I have no idea what you are off to but have FUN.

---

### Post by smo on 2010-04-08
hi

first, thansk for the infos 

i just tried it and i have 2 questions

how can i do the protect "only" the command line edit with the "e" key or console 

so anyone can boot, but only superuser can edit the menu, is it possible ?

and second question:

is it possible to change the keymap in grub2 ? i looked all the files but can t find anything for it

thx

++

---

### Post by drs305 on 2010-04-09
> **smo said:**
> 
how can i do the protect "only" the command line edit with the "e" key or console 

so anyone can boot, but only superuser can edit the menu, is it possible ?

...

is it possible to change the keymap in grub2 ? i looked all the files but can t find anything for it

I have very limited experience with the keymap issue. I know you can add items such as "keymap=us" or "keymap=qwerty" to either of these lines in /etc/default/grub:
> GRUB_CMDLINE_LINUX_DEFAULT=
GRUB_CMDLINE_LINUX=

I have also used "setkmap=us" in the linux line of a custom menu entry for mounting ISOs. That is the limit of my knowledge on keymaps in Grub2 I'm afraid.


As for the first question you asked, this is one of the things I like about the forums. Sometimes it takes a bit of thought to come up with a solution to an unanticipated request.

If a superuser and password are set the entire menu is locked for editing menuentries or entering the Grub2 command line. 

Here is what I came up with regarding your request - locking the edit feature (and also command line):

1. Make at least one scripted entry password-protected, such as the recovery mode. If there is one password-enabled entry, only the superuser can edit or use the terminal. No other entries would require any user to use a password.

2. A solution that meets your requirements (all entries accessible) could be done by adding an entry into /etc/grub.d/40_custom. You could make it invisible, or add a message either at the top or bottom of the real menu. (For the bottom, make the entry in 40_custom; for the top, rename the file 06_custom). The actual entry, other than the title, wouldn't boot to anything. I've used the "insmod ext2" command since it is already used in my existing grub.cfg entries.

Here are two examples.

Invisible:
> 
cat << EOF
menuentry " " --users *superman* {
insmod ext2
}
EOF


Welcome message in 06_custom:
> 
cat << EOF
menuentry "Welcome. You Have 10 Seconds to Select a New Entry." --users *superman* {
insmod ext2
}
EOF


Make sure you have added at least the *superuser* and password in the 00_header file as described in the first post and then update grub.

---

### Post by petteriIII on 2010-04-11
Thanks for your excellent Howto. I have been using the manual way of editing grub.cfg - the editing calls for helper-programs to pull trough and if you don't have them dont't even try. But when editing by hand there is no need to touch any configuration-files in any condition and there are no limits to what you can edit. But anyway password-protection operates just as you said. My grub.cfg in it's entirety is as follows:
  
set timeout=5
set default="Lucid-1, 2.6.32-18-generic, sda1" 
 
# Superuser petteri's password is 1234 in the context of editing menuline when booting or going to commandline; it is not the usual 'sudo-password'. Normal user osmo can boot Lucid-2 wit password 4321; other users cannot boot it at all.
set superusers="petteri"  
password petteri 1234    
password osmo 4321

menuentry "Lucid-1, 2.6.32-18-generic, sda1" --class ubuntu --class gnu-linux --class gnu --class os {
	insmod ext2
	set root='(/dev/sda,1)'
	search --no-floppy --fs-uuid --set df4b9966-28ad-41b3-936d-fa5470865131
	linux	/boot/vmlinuz-2.6.32-18-generic root=UUID=df4b9966-28ad-41b3-936d-fa5470865131 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-18-generic
}
 
menuentry  "Lucid-2, sda2" --users osmo {
	configfile (hd0,2)/boot/grub/grub.cfg
}

---

### Post by eotakos on 2010-08-02
Thank you very much for the how-to. I tried password protecting without encryption on lucid and it worked right away. I can't afford trying the risky encryption thing  because I am on vacation, without a live-cd, and my connection is over my mobile phone...

There was this trick suggested in the forums for the previous version of grub, in which instead of encryption, the permitions of menu.lst were changed in order to prevent unauthorized users from reading the unencrypted password from within the file.... could something like this work in this case? like changing the permitions of 00_header and grub.cfg files? (unfortunately I can't test it myself because I'd be left helpless without an OS in case of a failure... anyhow... I'll probably check this out when I get home)


Thanks again for the thread!

---

### Post by drs305 on 2010-08-03
eotakos,

I just did a simple "sudo chmod -r <path/filename>" on /boot/grub/grub.cfg and /etc/grub.d/00_header.  
```
sudo chmod -r /boot/grub/grub.cfg /etc/grub.d/00_header
```


Without the +r attribute, a normal user can't use "cat" or open the file for viewing without admin privileges.  The update-grub command worked fine and any of the commands combined with "sudo" or "gksudo" worked normally.

---

### Post by Jordy_224 on 2010-12-08
Hello, 

I preformed a fresh install, followed the directions and it worked. Thanks 

```
Ubuntu 10.04 on Dell
grub version  (GNU GRUB 1.98-1ubuntu9)

```

**Note:** 
It is very important for me that normal user accounts are blocked from reading access (grub.cfg, 00_header ... ect) since the password is visible.  

changed to  

```
sudo chmod 771 /etc/grub.d*

```

Its worth mentioning that as a result several "complaints" were upchucked at boot  ie. 
Don't understand EOF
Bad script 
Can't read script ....

However, I did not have trouble accessing the grub menu or entering password to edit to grub script. 


--Thanks again.

---

### Post by jhansonxi on 2010-12-23
To specify multiple users on a menu entry separate them by a comma:
--users superman,bill

---

### Post by drs305 on 2010-12-24
> **jhansonxi said:**
> To specify multiple users on a menu entry separate them by a comma:
--users superman,bill

jhansonxi,

Good tip. I hadn't provided an example of mulitiple non-*superusers*. I've added a note.

Thanks.

---

### Post by EnigmaticCoder on 2011-02-03
Password encryption worked for me without hangups. I did not need to use grub's console mode.

Grub 2 version 1.98+20100804-5ubuntu3

---

### Post by basarfraz on 2011-04-13
hi guys!

Here is a nice information, so pls share with other people.

---

### Post by scott-ian on 2011-04-15
Would it be possible to create a script that runs at start up that check the user list and updates the user names and passwords so you don't have to mess with the configuration files?

---

### Post by drs305 on 2011-04-16
> **scott-ian said:**
> Would it be possible to create a script that runs at start up that check the user list and updates the user names and passwords so you don't have to mess with the configuration files?

I'm not sure what you mean by checking and updating the user names/passwords. Since I don't know what you want, I can't say if G2 has the capability to accomplish it. 

The Grub2 passwords are just to allow/prevent starting a specific menuentry and the usernames aren't associated with the users of a specific OS. Offhand, it sounds more like what you want would be done at the OS's log in menu.

---

### Post by scott-ian on 2011-04-16
> **drs305 said:**
> I'm not sure what you mean by checking and updating the user names/passwords. Since I don't know what you want, I can't say if G2 has the capability to accomplish it. 

The Grub2 passwords are just to allow/prevent starting a specific menuentry and the usernames aren't associated with the users of a specific OS. Offhand, it sounds more like what you want would be done at the OS's log in menu.
I mean searching for the Ubuntu  user accounts, and updating the grub to match that setup.

---

### Post by drs305 on 2011-04-16
> **scott-ian said:**
> I mean searching for the Ubuntu  user accounts, and updating the grub to match that setup.

That would be do-able from within Ubuntu. The script would have to extract usernames and passwords, then add them and the user/superuser lines to the 00_header file. You would then use *sed* to revise the menuentries as generated in Step 4 of the original post.

So the answer to your question as to whether it's possible, the answer is yes. I'm not well versed in writing scripts, but the only thing I think would go far beyond the basics would be how to retrieve unencrypted passwords from Ubuntu if you wanted to fully automate the script. 

Whether it would be worth the time to write such a script rather than merely edit the grub files is another matter.

---

### Post by kakkerpolakke on 2011-06-25
Hey,

I have a little problem. I need to restart my root password on Ubuntu (GRUB 1.98)

I've followed instructions elsewhere, but it hasn't worked so far. Others basically said I should edit the kernel line that begins: init=

... but I simply don't have it here.

Thanks for any advice,
:)

---

### Post by drs305 on 2011-06-26
> **kakkerpolakke said:**
> Hey,

I have a little problem. I need to restart my root password on Ubuntu (GRUB 1.98)

I've followed instructions elsewhere, but it hasn't worked so far. Others basically said I should edit the kernel line that begins: init=

... but I simply don't have it here.

Thanks for any advice,
:)

Grub is a universal loader that doesn't deal with OS specific passwords. While you can add kernel options to the "linux" line in the menuentry (such as *quiet, splash, nomodeset, etc* I am not aware of the option that would deal with Ubuntu's root password settings. If you found one, it would be placed on the GRUB_CMDLINE_LINUX_DEFAULT="" line of /etc/default/grub. 

Here is one list of available kernel options:
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")

---

### Post by ranch hand on 2011-06-26
> **kakkerpolakke said:**
> Hey,

I have a little problem. I need to restart my root password on Ubuntu (GRUB 1.98)

I've followed instructions elsewhere, but it hasn't worked so far. Others basically said I should edit the kernel line that begins: init=

... but I simply don't have it here.

Thanks for any advice,
:)
If you mean that you must reset your root password take a look at;
```

man passwd

```
You will need to have a live CD (or another install on your box) and chroot to your install to use the commands to change a root pass word.

---

### Post by snooffy on 2011-07-22
This is exactly what I was looking for, protected all entries for recovery. 

I'm using GRUB 1.98 on Lucid Lynx and this guide worked flawlessly.

Thanks a lot! 

The question is, if someone would boot up the machine from a live CD will the still be able to change the GRUB configuration files and gain the root access that way?

---

### Post by drs305 on 2011-07-23
> **snooffy said:**
> The question is, if someone would boot up the machine from a live CD will the still be able to change the GRUB configuration files and gain the root access that way?

Yes they would. Physical access to a computer normally trumps security measures. 

You could add a BIOS password (if your BIOS allows it) so that access to any OS or CD is restricted, adding an extra level of security.

---

### Post by georgemc on 2011-07-29
DRS305: Thank you for this excellent guide.
 

 I can confirm that this all works with GNU GRUB version 1.99-9
 

 I also used this as a reference:
 

 [[FONT=LMRoman10]http://www.gnu.org/software/grub/manual/html_node/index.html[/FONT]]("http://www.gnu.org/software/grub/manual/html_node/index.html")
 

 Section:
 [15 [FONT=LMRoman10]Authentication and authorisation[/FONT]]("http://www.gnu.org/software/grub/manual/html_node/Security.html#Security")
 [21 [FONT=LMRoman10]Invoking grub-mkpasswd-pbkdf2[/FONT]]("http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dmkpasswd_002dpbkdf2.html#Invoking-grub_002dmkpasswd_002dpbkdf2")
 

 Straying a little from your guide, I added this at the end of 00_header:
 

 ```

 cat <<EOF
     set superusers="root"
     password_pbkdf2 root grub.pbkdf2.sha512.10000.biglongstring
 EOF
 
``` For the “biglongstring” use “password_pbkdf2” and cut&paste.
 

 And then I changed the menuentry's in 10|20|30 files to:
 

 ```

 printf "menuentry –users '' '${title}' ${CLASS} {\n" "${os}" "${version}"
 and
 menuentry –users “” "${LONGNAME} (${2}-bit) (on ${DEVICE})" {
 
``` You need to be careful with your quoting, inside the printf statement you need to use single quotes.
 

 By giving a “NULL string” to the “–users” options you only need to change the 00_header file when you change the password and then run update-grub.
 

 On a multi-boot setup your can have different users for the different OS's, therefore the idea to sync the passwords up with the password file is definitely worth while to look into.
 

 Of course all of this can be by-passed by simply using a CD/DVD like “super grub”, “plop”, or a “live CD”.  Again the old adage “physical access = root access” applies.  However, I fell it adds yet another layer to the onion called “security”; let them work for the access.
 

 Happy to contribute.
 

 George

---

### Post by drs305 on 2011-07-29
> **georgemc said:**
> 
 I can confirm that this all works with GNU GRUB version 1.99-9
 
 Happy to contribute.

 George

Thanks for the information. Good to know it still works in 1.99.

I'll try to digest your post and update the original post (with credit of course) if needed.

**Update:** Revised Section 7 on encrypted passwords.

---

### Post by ignisterra on 2011-12-15
I am new and it's been a long time there was no comment on this topic but I have a little question on the section about how to secure "Recovery Entries" for linux.
> 
**Password protect the *Recovery Mode* option**: [COLOR=DarkGreen]*/etc/grub.d/10_linux*[/COLOR]  Also make the change as described in the */etc/grub.d/00_header* section above. 
From (GNU GRUB 1.98-1ubuntu5):
     Quote:
                                                   [SIZE=1]printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"[/SIZE]
To:
     Quote:
                                                 if ${recovery} ; then
  printf "menuentry '${title}' --users *user1* ${CLASS} {\n" "${os}" "${version}"
else
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
fi                      I've changed the line printf "menuentry ... by the others but it doesn't work.
It was written: printf "**menuentry** '${title}' **--users *user1*** ${CLASS} {\n" "${os}" "${version}" but I wonder if it was rather that: printf "**menuentry --users user1** '${title}' ${CLASS} {\n" "${os}" "${version}" ?

Thank you in advance.

---

### Post by drs305 on 2011-12-15
*ignisterra*

Welcome to the Ubuntu Forums. :-)

As you found out, this guide was written when Grub 1.98 was very young. Thanks for pointing out that things have changed a bit, even in this older version of Grub.

I booted an old copy of Lucid, which still uses Grub 1.98, and updated it to the current Grub 1.98 package. 

The entry in 00_header does not appear to have changed, however the 10_linux entry is indeed a bit different now.

This is what I show as the default Grub 1.98 /etc/grub.d/10_linux default entry linux (approximately line 70).
>   if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")" 
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"


I wasn't sure about the exact format of your suggestion, so I just did some experimenting. The way I got it to work was to edit the "printf" line to include the user, add the that line in each conditional section, and remove it from the end. This is what worked for me (for user *drs305*):

> 
 if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")" 
[COLOR="DarkRed"]  printf "menuentry '${title}' ${CLASS} **--users drs305** {\n" "${os}" "${version}" [/COLOR]
  else
    title="$(gettext_quoted "%s, with Linux %s")"
[COLOR="DarkRed"]  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}" [/COLOR]
  fi


Don't forget to update-grub, and if you need to make sure you are using Grub 1.98 just run "grub-install -v".

If this works for you please let me know and I'll update the first post.

---

### Post by drs305 on 2012-07-03
Thread Closed.

This page has been migrated to the Ubuntu Community Documentation site. For the most up-to-date information, please visit:
[https://help.ubuntu.com/community/Grub2/Passwords]("https://help.ubuntu.com/community/Grub2/Passwords")

The above page is a sub-page of the main community documentation regarding [_Grub2_]("https://help.ubuntu.com/community/Grub2").

Thank you to all the users who posted in these threads and expanded our knowledge of Grub 2 since it's introduction.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12073029](http://ubuntuforums.org/showthread.php?p=12073029)

[B]
Support threads regarding the wiki and it's content should be created in a suitable forum.[/B]

---

