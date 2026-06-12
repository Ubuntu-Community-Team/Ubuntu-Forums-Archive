---
title: "Forum policy on log-in-as-root tutorials"
date: 2010-05-17
forum: Security
---

### Post by bodhi.zazen on 2010-05-17
The staff's "policy" or stance on this is IMO misunderstood by forum users.

This policy exists due to the number of new users of Ubuntu on these forms. This is a "Forums  policy" and should not be misconstrued as an "Ubuntu policy" or as the one and only method of system administration.

**The goal is to educate new users.**

[B][COLOR="#FF0000"]Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is  completely inappropriate and unnecessary.[/COLOR]
[/B] 
In terms of the root account, there are times when one needs to activate or set a root password. At such times setting a root password is acceptable.

The primary consideration is simply that we have a large influx of new users on these  forums.

Please refer new users to the [RootSudo]("https://help.ubuntu.com/community/RootSudo") wiki page. After reading the wiki page users will have gained the requisite knowledge and may decide for themselves how to manage their systems. This is the whole point of the policy, educate users and allow them to decide for themselves.

On the forums, however, in the past, before this "policy", all too often people would simply instruct new users to set a root password to "fix" their problems. This was done without explaining (not intended as an exhaustive list):

[LIST=1]
[*]The potential risks of setting a root PW.
[*]How to lock the root account.
[*]The nature of the problem and the preferred solution, ie linux  permissions, fstab, etc.
[*]Setting a root PW can (or has in the past) caused new problems.
[/LIST]
Thus the intent of the policy is we prefer if people educate new users re: permissions, etc, etc, rather than simply instruct them to set a root password.

The preferred method of obtaining a root shell is :

```
sudo -i
```See : [This post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4") by [unutbu]("http://ubuntuforums.org/member.php?u=518895") for details.

As of Bionic (18.04), old graphical privilege-escalation tools like [FONT=Fixedsys]gksu[/FONT] and [FONT=Fixedsys]pkexec[/FONT] have been deprecated. In fact, the [FONT=Fixedsys]gksudo[/FONT] package has been deleted from all Bionic and later repositories.

For default installs, the official way to escalate to root is to use command line tools prepended by [FONT=Fixedsys]sudo[/FONT]. We can only surmise that the developers decided on this restriction to avoid the sort of problems that new users unintentionally but routinely create for themselves by running graphical applications as root.

Whether one agrees with this strategy or not, when taking on the responsibility of advising new users, the default state of the operating system needs to be acknowledged and accounted for. Advice that departs from this default should only be given out with very careful caveats and the willingness to provide support should something go wrong.

[FONT=Fixedsys]gksu[/FONT] has not been updated since 2009. This in itself is problematic because code that goes unreviewed for so long is a potential security risk. [FONT=Fixedsys]gksu[/FONT] has been superseded by [FONT=Fixedsys]pkexec[/FONT] for all flavours of 'buntu. However, only the *Xubuntu* developers have elected to allow the root elevation of *Thunar* and *Mousepad* to be invoked with [FONT=Fixedsys]pkexec[/FONT]: see example below.

*Kubuntu* has made it easy to launch a root file manager. In the KDE launcher, under "Computer", a root version of the *Dolphin* file manager is already included. Opening a text file in root *Dolphin* will, in turn, launch a root *Kate* for editing: see example below.

In all remaining flavours, the editor and file manager do not ship with *PolicyKit* files. Therefore, it is not possible to invoke [FONT=Fixedsys]pkexec[/FONT] by default for any other flavours.

There are several workarounds for this:

[LIST=1]
[*]If a user desires the comfort of a quasi&#8209;graphical environment and is prepared to run a simpler command&#8209;line app, then *Midnight Commander* running in a root shell may be sufficient. *Midnight Commander* is not part of a default 'buntu install, but is available in the repositories: see example below.
-
[*]The python extension [FONT=Fixedsys]nautilus&#8209;admin[/FONT] will add two extensions to *Nautilus*. These extensions add the option to launch root windows of both *gedit* and *nautilus* from within a regular instance of *nautilus*: see example below.
-
[*]*PolicyKit* files for both *gedit* and *nautilus* can be added to the [FONT=Fixedsys]polkit[/FONT] directory. This will allow either *gedit* or *nautilus* to be launched as root with either of:```
pkexec gedit
pkexec nautilus
```
Instructions and links for adding the required *PolicyKit* files can be found in [this WebUpd8 article]("http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html").

Knowledgeable users could conceivably build working *PolicyKit* files for other editors and file managers by using the referenced files as a template. They are simple XML files that can be edited with a standard text editor.

Note that although this workaround does launch root instances of these apps, it also produces warnings and alerts about files missing in the root home directory that point to how alien and brittle this workaround may be.
-
[*]It is possible to use [FONT=Fixedsys]sudo[/FONT] with graphical apps like *gedit*, *nautilus*, *leafpad*, *pcmanfm*, etc **provided you use the** [FONT=Fixedsys]-H[/FONT] **flag**. The use of this flag is critical: it properly sets root to its own environment instead of improperly inheriting the user's environment. Use of the [FONT=Fixedsys]-H[/FONT] flag is mandatory. Failing to use it may corrupt critical system files and prevent you from logging in.

With [FONT=Fixedsys]sudo -H[/FONT] almost any graphical app can be launched under root within any 'buntu flavour. This includes each flavour's default graphical editor and file manager: see example below.

As is the case with defining *PolicyKit* files for [FONT=Fixedsys]pkexec[/FONT], this workaround produces similar warnings and alerts about expected files that are missing in root's home directory, and raises similar concerns about brittleness. Additionally, careless use of this workaround could risk system breakage if one forgets the [FONT=Fixedsys]-H[/FONT] flag&#8212;an easy omission to make.
[/LIST]
**Mixed examples of how to run the default file manager/editor as root:**

[COLOR="#FF0000"]Ubuntu/Gnome/Budgie:[/COLOR]
```
sudo apt install nautilus-admin
```
Then: nautilus &#8594; <right click> on directory or file &#8594; "Open as Administrator" or "Edit as Administrator"

[COLOR="#FF0000"]Xubuntu:[/COLOR]
```
pkexec thunar
pkexec mousepad
```

[COLOR="#FF0000"]Lubuntu  :[/COLOR]
```
sudo apt install mc
sudo mc
sudo nano
```

[COLOR="#FF0000"]Ubuntu-Mate[/COLOR]
```
sudo -H caja
sudo -H pluma
```

[COLOR="#FF0000"]Kubuntu[/COLOR]
Launcher &#8594; Computer &#8594; Root Dolphin (&#8594; Edit file)


If you wish to instruct people to set a root password please include, at a minimum, the nature of the problem at hand (permissions) and information on how to [lock the root account again]("https://help.ubuntu.com/community/RootSudo#Re-disabling_your_root_account").

Additional discussion staff input is located [here]("http://ubuntuforums.org/showthread.php?t=716201") (this is a link to the "old" sticky by [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")).

HTH =)

---

