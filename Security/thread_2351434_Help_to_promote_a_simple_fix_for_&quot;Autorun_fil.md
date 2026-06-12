---
title: "Help to promote a simple fix for &quot;Autorun files from Removable Media&quot;"
date: 2017-02-03
forum: Security
---

### Post by johnmne on 2017-02-03
Hi everyone,

There is a simple "bug" in Ubuntu for years, which allows _by default_ to execute programs from external media (USB or CD..).
It means that every person that installs Ubuntu and didn't change the default values - is affected by this bug.

The fix for this should be easy and quick.

Please help to promote the fix by clicking on the following URL:
[https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/1617620](https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/1617620)
(Bug #1617620 in launchpad)

and in that page - click on the green link "This bug affects 1 person. Does this bug affect you?"
(The number of affected people may vary obviously.)

Thank you!

---

### Post by howefield on 2017-02-03
Can you provide an example of an application automatically executing upon insertion of a USB stick ?

Perhaps I am misunderstanding your post.

---

### Post by johnmne on 2017-02-03
Hi howefield,

I don't remember the specific details, but:

It is known that you can prepare a CD with "NTFS partition" (or some other Windows-like partition) that allows to automatically execute a program when it is inserted to the PC.

This is a known weakness of Windows that happened about 10 years ago (?) and everybody "laughed" at MS for that back then..

The same applies to a USB if it is prepared the same way like a CD.

---

### Post by howefield on 2017-02-03
> **johnmne said:**
> I don't remember the specific details, but:.

Sigh.... <shrug>

---

### Post by nothingspecial on 2017-02-03
The default, as in what happens after a fresh install, is to ask you what you want to do. It then suggests some relevant software for cds, dvds, phones with pictures etc. Maybe it does for usb drives too, I don't recall it doing so but I'm not saying it doesn't. Possibly it detects image files and asks if you want to open shotwell.

Anyway, this is not a bug, it's a choice. You can choose to open rhythmbox when you insert a cd or choose to do nothing. In my experience inserting a usb stick opens nautilus (or files or whatever it's called these days). This is "executing a program". It certainly doesn't execute a program on the drive, that's a whole different thing.

If you wanted to execute a program after inserting a usb drive then you can write a script to do this, but Ubuntu does not do this by default.

---

### Post by johnmne on 2017-02-03
[**[COLOR=#990303][B]howefield**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=186490"):
sorry but as you can see the bug report was opened a while ago.

---

### Post by johnmne on 2017-02-03
[**[COLOR=#DD4814][B]nothingspecial**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=491516"):
No, I think you don't understand:
Please try to go to:
1. In Ubuntu 16.04, go to Settings -> Details.
2. In the left pane choose "Removable Media".
3. On the right pane you'll see "Software", while the value in the drop-down menu is "Run Software".

You wrote:
"In my experience inserting a usb stick opens nautilus"
But in order to execute a program automatically when inserting a USB stick, you need to create an "autorun.inf"-like file, or create a specific Windows partition (I think it is FAT32).
Sorry, I thought you were familiar with those things, it seemed to be a known problem.

---

### Post by howefield on 2017-02-03
> **johnmne said:**
> ...sorry but as you can see the bug report was opened a while ago.

A few months and with equally little detail as this thread ....

---

### Post by The Cog on 2017-02-03
The XML description of the option says:
>     <key name="autorun-x-content-start-app" type="as">
      <default>[ 'x-content/unix-software' ]</default>
      <summary>List of x-content/* types where the preferred application will be launched</summary>
      <description>List of x-content/* types for which the user have chosen to start an application in the preference capplet. The preferred application for the given type will be started on insertion on media matching these types.</description>

So it's nothing like autorun.inf - it doesn't run software on the inserted media, it runs the preferred application (e.g. a video player, pdf viewer etc) for whatever type of media has been inserted. Although with a bit of effort you might be able to configure it to open script files with a script interpreter if you really wanted.

---

### Post by HermanAB on 2017-02-04
Linux doesn't protect you against yourself, but a default install will not autoexecute programs from removable media.

---

