---
title: "[HOT] PCManFM 0.4.4 with Samba, SSH, and FTP support!!!"
date: 2008-05-17
forum: The Cafe
---

### Post by PCMan on 2008-05-17
Here is a screenshot of the latest PCManFM in development.
As you can see, now we have **remote file system** support (under development) and **compact list view**(already available in 0.4.1.1 stable).

[IMG]http://people.linux.org.tw/~pcman/lxde/pcmanfm_fuse.png[/IMG]

GnomeFiles project page: [http://www.gnomefiles.org/app.php/PCMan_File_Manager]("http://www.gnomefiles.org/app.php/PCMan_File_Manager")

SourceForge project page: [http://pcmanfm.sourceforge.net/]("http://pcmanfm.sourceforge.net/")

LXDE project page (PCManFM is core component of LXDE project): [http://lxde.org/]("http://lxde.org/")

**Warning: This is NOT a stable release. Use it at your own risk**

This is the first release of FUSE experimental branch.

**What's new?**
* Mount remote file systems via ftp, ftps, sftp, and samba with user-friendly GUI. (utilize FUSE technology)
* Some minor bug fixes.

**Note:** FTP/FTPS support is provide by curlftpfs. SFTP support is provided by sshfs. Samba support is provided by fusesmb. To use those new features, curlftpfs, sshfs, and fusesmb must be installed.

Besides, for FUSE to work, you must be a member of group 'fuse'. Otherwise, you'll get "permission denied". For detail, please refer to the documentation of FUSE.

**Security Concerns**:
* When using ftp and ftps with curlftpfs, the username and password will be passed in the command line, so they are clearly visible with 'ps' command. Use this with cautions.
* The usernames and passwords are stored in ~/.config/pcmanfm/remote-fs.list in **plain text** without encryption. The permission of that file is 0600, so only the owner and root can view it. However, there are still risks. Please keep this in mind.

LXDE rocks!! :)

---

### Post by cardinals_fan on 2008-05-17
Looking good!

---

### Post by blithen on 2008-05-17
Yeah no kidding. Keep up the good work. This looks like it can turn into something great.

---

### Post by eriqjaffe on 2008-05-17
This is so many different kinds of awesome, I don't even know where to begin.

---

### Post by PCMan on 2008-05-18
> **cardinals_fan said:**
> Looking good!
So, does this work well? Anyone really tested it?
We need some comments and bug reports. Patches are even more welcomed.
Thanks. :-)

---

### Post by cdekter on 2008-05-18
I've been waiting for a decent SCP/SFTP-enabled file manager - I'll start testing/using this at work starting tomorrow and report back! :D

---

### Post by eriqjaffe on 2008-05-19
> **PCMan said:**
> So, does this work well? Anyone really tested it?
We need some comments and bug reports. Patches are even more welcomed.
Thanks. :-)I haven't tried connecting to a Samba share, but I was able to connect to FTP over SSL and send & receive data just fine.  However, when I attempted to "disconnect" via the context menu, I just get this:

[IMG]http://img260.imageshack.us/img260/2558/25kn7.png[/IMG]

Also, clicking on "Network Neighborhood" killed PCManFM until I install fusesmb - I figured that out by watching the terminal, but the GUI should pop up a dialog box stating that you need to install fusesmb rather than just quitting.

Other than that, I'm loving it.

---

### Post by eriqjaffe on 2008-05-19
So...maybe it's just me, but my Network Neighbourhood is empty, even though I have a system running a samba server downstairs (I didn't have it on last night).

Remote Host Settings just give me the option for FTP, FTPS and SFTP, should I be seeing SMBFS in there?  I've verified that I'm a member of the FUSE group...

---

### Post by cdekter on 2008-05-22
I started playing with this today... discovered what might be a small bug. If I connect to an FTP site with a backslash in the username, I have to escape the backslash myself like so:

user\\name

instead of just

user\name

Is there a bug tracker for PCmanFM that I can file a bug?

---

### Post by John.Michael.Kane on 2008-05-22
> **cdekter said:**
> I started playing with this today... discovered what might be a small bug. If I connect to an FTP site with a backslash in the username, I have to escape the backslash myself like so:

user\\name

instead of just

user\name

Is there a bug tracker for PCmanFM that I can file a bug?

[PCMan File Manager Bug Tracker]("http://sourceforge.net/tracker/?group_id=156956&atid=801864")

---

### Post by cdekter on 2008-05-24
Just an observation at this point (as I don't mind it that much) but it seems Nautilus has been replaced by PCManFM as the handler for all my bookmarks (such as Home, Document etc). Computer, Network, etc are still opening in Nautilus. I haven't done anything to make this happen - it seems to have just happened as part of the 'make install'. Is this expected?

---

### Post by PCMan on 2008-05-24
> **cdekter said:**
> Just an observation at this point (as I don't mind it that much) but it seems Nautilus has been replaced by PCManFM as the handler for all my bookmarks (such as Home, Document etc). Computer, Network, etc are still opening in Nautilus. I haven't done anything to make this happen - it seems to have just happened as part of the 'make install'. Is this expected?
PCManFM just claimed to support "x-directory/gnome-default-handler" in pcmanfm.desktop. Other than that, make install didn't do anything.
I just noticed that Thunar does this in its Thunar.desktop, so I did it, too. Another problem is, without this, Firefox will try to open the folders of downloaded files with nautilus in any case. Although there was some config can be done in about:config of Firefox, this doesn't work anymore in Firefox 3. All programs using gnome-vfs will try to find file managers supporting "x-directory/gnome-default-handler", which should only be Nautilus if no other file manager adds this. There is no other way to change the file manager being launched by gnome-vfs. So, this is a dirty hack to overcome the design flaw of gnome-vfs who only recognize Nautilus by default.
This can be fixed by editing "~/.local/share/applications/defaults.list", and add these lines:
```

[Default Applications]
x-directory/gnome-default-handler=nautilus --no-desktop

```
If you find this anonying, bug report to gnome team, and ask them to improve gnome-vfs and make it compatible with other file managers. At least they should let the users choose their favorite file manager.

---

### Post by keisangi on 2008-06-06
pcmanfm 0.4.4 is really good..
fast, small, efficient

pcmanfm shows things could be done the right way, without all the bloat!
it's a example on how things should be done on linux imho.

thanks for this good program

---

### Post by graabein on 2008-06-10
I have an idea for PCManFM: "Overwrite older" option when copying from A to B. 

I might have two very similar directories I want to sync, but I don't want to overwrite every big identical file, or decide which file I should skip or not. So doing a date compare between file1 and file2 and overwriting B if A is newer.

Sounds good?


Off course this is not an original idea, I've seen it in other programs like [Total Commander]("http://www.ghisler.com/").

---

### Post by lestrade on 2008-06-13
I love Total Commander (Windows). Ghisler, the author, has done a great job developing it.  I *really* want to find an Ubuntu equivalent. "Overwrite Older" is very safe that keeps me from accidently erasing the new file with an older one. Any suggestions for an equivalent? thanks, JP

---

### Post by quanumphaze on 2008-06-14
I know PCManFM can draw the desktop but does it have any support for multiple wallpapers that works with Compiz.

It's the only thing I really hate about Nautilus. There was a patch for Nautilus that made the background transparent and let Compiz draw the wallpaper instead but that patch no longer works with 2.22

Can PCManFM support real multiple wallpapers or at least background transparency?

---

### Post by mrjohnston on 2008-06-14
It's amazing how many times I impress myself with my own stupidity.  Very impressive work.  Thank you PCMan for fixing most of the issues I had with nautilus, and for your work on LXDE as well (which is the best low resource DE-like experience out there).

---

### Post by Cherry Cotton on 2008-07-04
> **cdekter said:**
> Just an observation at this point (as I don't mind it that much) but it seems Nautilus has been replaced by PCManFM as the handler for all my bookmarks (such as Home, Document etc). Computer, Network, etc are still opening in Nautilus. I haven't done anything to make this happen - it seems to have just happened as part of the 'make install'. Is this expected?

This happened to me, too. How can I change it back?

---

### Post by shnifti on 2008-08-10
FTP and SSH works for me. I haven't tested SMB yet.
But while disconnecting the shares, I get the same error like ejiqaffe:
[IMG]http://img260.imageshack.us/img260/2558/25kn7.png[/IMG]
Is this already fixed? Is there anyone who can disconnect the mounts without troubles?
For the future a twinview mode like gnome- or total-commander offers would be great.
Otherwise great work PCMan
greetz Shnifti

---

### Post by andrewjoy on 2008-08-17
Quite nice i am a big big fan of PCmanFM as its lightwieght easy to use and just works :). This is a nice idea to add in but try not to go too far and add loads of fetures.

---

### Post by Panthios on 2008-08-17
How can you get PCManFM to connect to a FTP site??
Are you just typing [ftp://address.com](ftp://address.com) in the addressbar?

Im using Arch with LXDE, PCManFM 0.5.0

---

### Post by chris4585 on 2008-08-17
which version of pcmanfm can you choose to have the openbox menu work on the desktop?

---

### Post by eriqjaffe on 2008-08-17
> **chris4585 said:**
> which version of pcmanfm can you choose to have the openbox menu work on the desktop?Any recent version, AFAIK.  On the Desktop tab of the Preferences, makes sure that "Show menus provided by WM when desktop is clicked" is checked.

---

### Post by notfonk on 2009-01-29
hey there.

I just installed LXDE, wich looks great on my modest box :)

Problem is, I can't find any trace of the samba feature. How do you use it? Am i right to think it's not active in 0.5 , and if so, why ?

I'd love to use it, cause i'm stuck using smbmount manually, or using nautilus, wich is quite slow.

i searched everywhere, but there is no doc on the subject at all , so i came to ask here. Also, is the project dead ? Last update was 7 monthes ago, there is no sign of any evolution anywhere

If anybody knows what pcman is up to :)

---

### Post by notfonk on 2009-01-29
oh nvm the "Did pcman disappear" part of my question, he is just working on LXDE as it appears, which is just fine with me :P

So i guess we'll see samba in pcmanfm in due time, and i'll keep on with the CLI in the meantime

---

### Post by redhalo on 2009-02-05
> **notfonk said:**
> oh nvm the "Did pcman disappear" part of my question, he is just working on LXDE as it appears, which is just fine with me :P

So i guess we'll see samba in pcmanfm in due time, and i'll keep on with the CLI in the meantime

So, are we confirmed that samba doesn't work in the current version? I'm not really sure how to access my network with pcmanfm either.

---

### Post by kaczus on 2009-04-19
> **redhalo said:**
> So, are we confirmed that samba doesn't work in the current version? I'm not really sure how to access my network with pcmanfm either.

It seems it's only included in the pcmanfm-experimental:
[http://sourceforge.net/project/showfiles.php?group_id=156956&package_id=265937]("http://sourceforge.net/project/showfiles.php?group_id=156956&package_id=265937")
You need to compile it yourself. It's a regular "./configure && make && make install" thing.
ssh & ftp work for me, but I still need to figure out how to make it see smb shares

---

### Post by toupeiro on 2009-04-19
Looks like a very sweet application!  I tried to pull down the source and take a stab at it.  I'm running Jaunty x64-bit.  I red the instructions on the webpage and installed the dependencies I did not already have.  It built ok, no major errors, but when I launch it I am getting a segmentation fault.  Is your app supported on the 64-bit platform?

---

### Post by sefs on 2009-04-19
> **shnifti said:**
> FTP and SSH works for me. I haven't tested SMB yet.
But while disconnecting the shares, I get the same error like ejiqaffe:
[IMG]http://img260.imageshack.us/img260/2558/25kn7.png[/IMG]
Is this already fixed? Is there anyone who can disconnect the mounts without troubles?
For the future a twinview mode like gnome- or total-commander offers would be great.
Otherwise great work PCMan
greetz Shnifti

I thought I read earlier you needed to install fusesmb to get around that error.

---

### Post by aadansh on 2010-08-08
May this help you.

[http://pankajdangi.com/2010/07/how-c...ains-remotely/]("http://pankajdangi.com/2010/07/how-can-i-access-my-ftp-contains-remotely/")

---

