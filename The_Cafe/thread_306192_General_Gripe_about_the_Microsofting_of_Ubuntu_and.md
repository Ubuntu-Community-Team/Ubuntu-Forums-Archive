---
title: "General Gripe about the Microsofting of Ubuntu and Linux in general."
date: 2006-11-24
forum: The Cafe
---

### Post by rcrook on 2006-11-24
Ignore if you feel like. 

I just upgraded from dapper to Edgy the hard way. IE: I downloaded the live/install CD iso and re-installed from scratch. (I like a challenge.)

Anyway after installing from the CD I went to edit the fstab to add the other file systems on my pc and a couple of nfs mounts and what did I find in the fstab??!?!?!?

This:

[FONT="Courier New"]UUID=5384420f-f9ae-458e-b633-adfcb197cb6a / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1[/FONT]

The one thing that I have **loved** about UN*X and Linux since I started playing with them in 1993, is the easy of customizing the OS.  This ease is born out of the fact that 95% of all the configuration is done through flat **human readable** text files.

You just fire up your favorite editor and hack to your hearts content. This use of flat **human readable** text files for config has made UN*X/Linux the incredibly versatile OSs they are.

What the hell is UUID=5384420f-f9ae-458e-b633-adfcb197cb6a supposed to mean?????. Geez, did someone let a Microsoft developer loose on Linux??

This move towards using hashes and hex keys may be efficient for the OS itself but why cant the developers keep them **Out** of the configuration files humans may actually want to edit. The ability to hack at the configurations of different parts of the OS and Apps is one of the founding ideas for Unix like OSs. The more you alienate the user from this process the less people you have to contribute to the community. 

Now the really stupid thing about this example is that you **don't have to have** this ridiculous hash placed in the fstab. I changed the reference back the the good old /dev/hda1 and everything still worked fine. So my question is why place the hash in there in the first place?

Sigh. Microsoft has been doing this type of thing for years now. Slowly hiding the configuration options to the point that you cant make windows do the things you want without paying for expensive training or specialized software. 

So I am begging all you great developers out there, even if it requires a little extra coding, please please keep the config files in a **Human Readable** format??? Please???

;) 

Randall.

---

### Post by Tilex on 2006-11-24
> UUID=5384420f-f9ae-458e-b633-adfcb197cb6a

One can guess that this is your partition represented with some number, no?  I don't think config files are starting to become human unreadable and you will be able to customize your system as much as you want for as long as this is open source...

Linux is very different from Windows in the way it is designed, structured, implemented, not only because of config files being human readable.  But I agree that if there is a tendancy to 'hide' configuration options, it must be stopped. :)

---

### Post by cilynx on 2006-11-24
The UUID declaration is part of the automagic device munging that makes Ubuntu Just Work.  I can't say that I understand it, and I too am annoyed at the obfuscation being weilded onto my old friends.  However, I also understand that this stuff Just Works even when you switch around handware whereas our friendly /dev/hda1 will fall apart if our root is no longer located at /dev/hda1.

---

### Post by 23meg on 2006-11-24
Just on top of each line, I still see the usual device names commented out for reference, and yes, substituting them with the hash still works, and that makes the file human readable and editable by my definition. If those commented out lines weren't there, I'd agree that it wasn't human readable by default, but they are. Maybe you just missed them.

---

### Post by rcrook on 2006-11-24
I do understand that there are wonderful volume management tools out there. What I am asking the developers to take into consideration is how their work is to be presented to the humans. Purely as an example in this case, why use the hash to represent the root file system? why not code it to use say /dev/root?

The point I am trying to make is you don't have to use things like hashes in config files. Its easier on us non-developers to use more readable representations in the files we will be hacking.

I don't mean to offend anyone, its just a request for a little more thought be given to the numb skulls, like me, who will be coming along later to play with these things.:)

Randall.

---

### Post by TheFlamingBush on 2006-11-24
> **cilynx said:**
>  obfuscation 


Lovely word mate!....i just love this word, and its so rarely used these days! ...well done, 3 stars!!!:KS :KS :KS 

;)

---

### Post by rcrook on 2006-11-24
Obfuscation! that's the word I was looking for!! :)

---

### Post by 23meg on 2006-11-24
[QUOTE=rcrook]What I am asking the developers to take into consideration is how their work is to be presented to the humans. [/QUOTE]I don't understand in what way ```
# /dev/sda3
UUID=995bf9a9-4ae6-4e71-30db-905d2f342ada /               ext3    defaults,errors=remount-ro 0
```is less human readable and editable than ```

/dev/sda3               ext3    defaults,errors=remount-ro 0       
```Yes it *looks* busier, but isn't any less comprehendible to someone who has previous knowledge of the old /dev/XYZ format. For someone who doesn't, obviously both would be unintelligible. 

The only compromise here is a slightly more busy look for the technical user. You can read about the benefits [here]("https://wiki.ubuntu.com/ProbeForRootFilesystem") and [here]("http://enterprise.linux.com/comments.pl?cid=91642&sid=37323"). A good compromise if you ask me, and a far call from "Microsofting".

A comment with an explanation of the UUID hash right in fstab would have been nice though.

---

### Post by cilynx on 2006-11-24
To approach the readability question from a couple of different angles:

In example B, I can tell you what every word in the sentence does.  Say I want to switch around some drives and sda3 is going to be sdc3 in the new setup.  In example B, I can just make the change.  In example A, I have no idea how to change that UUID hash to point to sdc.  I wouldn't expect that it's possible without using the code that generated it in the first place.

Secondly, for those of us who hand-tune our config files, we know that comments aren't always true.  They're supposed to be, but it's not always the case.  Say I do figure out how to change that hash to what I want.  In my frustration with hash code, I forget to change the comment.  Now when I go to look at the file 6 months from now, I don't have any idea where my root filesystem is.

---

### Post by 23meg on 2006-11-24
[QUOTE=cilynx]In example B, I can tell you what every word in the sentence does.[/QUOTE]I agree that the second example is clearer. As I said, if there was an explanation that said "the UUID points to your device in this version of Ubuntu", it would make things clearer in the first example, but to someone who's aware that the /dev/XYZ bit used to come first in the fstab lines before and knows why things are commented out in general, it should make sense. [QUOTE=cilynx]I wouldn't expect that it's possible without using the code that generated it in the first place.[/QUOTE]I think as a technical *nix user you're expected to know that the fstab specification wouldn't change overnight. If you're a non-technical user, the new system takes care of things so that you won't have to fiddle with them anyway.

[QUOTE=cilynx]
Secondly, for those of us who hand-tune our config files, we know that comments aren't always true. They're supposed to be, but it's not always the case.[/QUOTE]Here you're expected to know that the commented out device name is the autodetected one. Again, if a comment made this explicit, it would be better. [QUOTE=cilynx]In my frustration with hash code, I forget to change the comment. Now when I go to look at the file 6 months from now, I don't have any idea where my root filesystem is.
[/QUOTE]Maybe there's something I don't follow here, but the comment only says where your filesystem was detected at install time. And if you explicitly change the hash to a certain device name, that's where your filesystem is at any given time of viewing the fstab. Please put it in different terms if I don't seem to be getting it (which is possible, I'm tired).

---

### Post by AndrewMc on 2006-11-24
> **cilynx said:**
> To approach the readability question from a couple of different angles:

In example B, I can tell you what every word in the sentence does.  Say I want to switch around some drives and sda3 is going to be sdc3 in the new setup.  In example B, I can just make the change.  In example A, I have no idea how to change that UUID hash to point to sdc.  I wouldn't expect that it's possible without using the code that generated it in the first place.


The [UUID]("http://en.wikipedia.org/wiki/UUID") is a unique identifier that is embedded in the filesystem. This means that even if you physically move the drive that the filesystem is on, the operating system will still find it. So if you want to rearrange your hard drives, just go ahead and you shouldn't(!) need to change fstab at all.

You can find the UUID of a partition near the top of the output of dumpe2fs. E.g.

```
sudo dumpe2fs -h /dev/hda2
```

> **cilynx said:**
> 
Secondly, for those of us who hand-tune our config files, we know that comments aren't always true.  They're supposed to be, but it's not always the case.  Say I do figure out how to change that hash to what I want.  In my frustration with hash code, I forget to change the comment.  Now when I go to look at the file 6 months from now, I don't have any idea where my root filesystem is.

For this, use "findfs":
```
sudo findfs UUID=3424ce2b-b7b2-4dcd-9ca6-2258a9f236b5
```

It's a teeny bit of effort to learn at the start, but makes the whole system more resiliant to hardware changes. I must admit to being a bit taken aback myself when I first saw it, but I'm over it now ;)

---

### Post by cilynx on 2006-11-24
Glorious.  I have been educated.

That explanation should be the comment in /etc/fstab.

---

### Post by aysiu on 2006-11-24
I was annoyed, too, by this shift, but I don't see it as obscuring anything, given that the old method still works and the comment above the gibberish code tells you where the device is located.

Do you have other examples of this supposed "Microsofting of Ubuntu and Linux in general"? Or is just the /etc/fstab in Ubuntu Edgy?

By the way, I moved this to the Cafe, as it is not really a support question.

---

### Post by CoolHand on 2006-11-24
I see the point of the UUID addition but in general I agree totally with the original post.  I have been using Unix and now Linux for a long time and I have also seen a shift recently in the design of many parts of the more popular systems included in most distros.  The most obvious examples are where databases are used to store user configuration settings.  I don't care if the database is of simple design.  I disagree with the concept completely.  To move user or application settings into any database to me sounds like a concept touted over ten years ago by MS called a "registry".  I have always liked simple text files for storing settings etc.  I will even accept XML files as they are plain text and easily understood.  No databases for settings!  No goofy codes to refer to various settings!  One mistake, one corrupt entry and everything is broken and you can't just mount it from a recovery disk and edit it.

---

### Post by rcrook on 2006-11-24
Ok, While I do understand why the changes has been made and that the id'ing of the fs is a good thing, what I don't understand is why a hash and not just a really nice easily readable identifier like say "UUID=Ubuntu-Root" for example. Even a id like "UUID=Seagate-ST3400N-root-1"? At least that is descriptive enough for dumb humans like me.:)

:)

Randall.

---

### Post by rcrook on 2006-11-24
> **aysiu said:**
> Do you have other examples of this supposed "Microsofting of Ubuntu and Linux in general"? Or is just the /etc/fstab in Ubuntu Edgy?
Not in the config files I have played with so far. But I have noticed a trend in the gui side of the environment. Gnome in particular is very much lacking in easily accessible config options. Its why I use KDE as I can mess with a lot more of the eye candy options quickly and easily.

I do understand the need to simplify the User interface, making is more attractive to non technical people. But the addition of and "Advanced" mode of config page would be a good compromise.

But even in KDE I have noticed changes that remove options that would be useful. An example is the esd config under amarok. Back in breezy when the default engine was gstreamer I could actually specify the remote esd host when configuring the output engine. When the engine was changed to xine I lost that option. I am sure if I mess long enough I will find the right config file for xine where I can manually set it, but the whole idea of hiding these types of options smacks of Microsoft's innate ability to hide such details in the registry.

The reason I spoke out is that when I vi'd the fstab and saw the hash the first thing that came to mind was it looked exactly like something you would find trolling through the windows registry.

The thought of having Linux follow Windows towards configuration data being stored in such a user "unfriendly" fashion, like the "registry" just got under my skin. If you get my drift.
 
> **aysiu said:**
> By the way, I moved this to the Cafe, as it is not really a support question.

Sorry I placed it in the wrong area. I am new to the forum. 

:)
Randall.

---

### Post by 23meg on 2006-11-24
> **rcook]
Ok, While I do understand why the changes has been made and that the id'ing of the fs is a good thing, what I don't understand is why a hash and not just a really nice easily readable identifier like say "UUID=Ubuntu-Root" for example. Even a id like "UUID=Seagate-ST3400N-root-1"? At least that is descriptive enough for dumb humans like me.[/QUOTE]But it's not descriptive enough for the computer. Every formatted filesystem has an UUID said:**
> 
The reason I spoke out is that when I vi'd the fstab and saw the hash the first thing that came to mind was it looked exactly like something you would find trolling through the windows registry.In other words it was an instant reaction based on the looks of the UUID. I don't mean to sound harsh; you just seemingly rushed in your judgement and missed the commented out device names. And sure, a comment at the start of the fstab file that detailed the changes would make them harder to miss.

---

### Post by RRS on 2006-11-24
> .....a comment at the start of the fstab file that detailed the changes.....

From this and previous threads I think I have a fair understanding of the change and the reasons behind it.

What I don't have is the background to confidently write the explanation.

If someone with better knowledge and lanquage skills could provide a basic "comment/explanation" I'd gratefully add it to my fstab file.

Seems likely others would appreciate the effort also, so thanks in advance if an expert has some spare time.

---

### Post by rcrook on 2006-11-24
> **23meg said:**
> But it's not descriptive enough for the computer. Every formatted filesystem has an UUID; this has been so for years, and the new system just searches for filesystems by UUID instead of device identifier or label.

That's fine but my question still stands, why a hash and not a descriptive ID? Characters are just hex codes too. Would it be so hard to replace the algorithm that generates the hash with code that allows for a human readable ID to be made and used? Seriously, I don't see why we should be to lazy to try and keep a file format convention "fstab" (which has been around for a lot longer than ext3) just because its easier to knock up a hash generation algorithm than it is to write some code that generates a descriptive id.
 
> **23meg said:**
> In other words it was an instant reaction based on the looks of the UUID. I don't mean to sound harsh; you just seemingly rushed in your judgment and missed the commented out device names. And sure, a comment at the start of the fstab file that detailed the changes would make them harder to miss.

Its not harsh at all. But a little off the mark. I did see the comments. And once again my disallusion in seeing the hash is still justified based on my comments above. The convention in the past has been to, to a large extent, keep the configuration files fairly simple and easy to read. And the fstab convention is a fairly good and valid one. The LABEL directive that was introduced with ext3 a few years back was a good one. It allowed for moving disks and filesystems and was easy to read. Yes, you have to set the label purposely but what price is that? Using the UUID for the same purposes is easier because you can just use the one generated at the time the fs is created. But I think if you are going to use it, it would be so much better if the UUID was more human friendly then just a hash.

LOL, If I had the motivation, intelligence and coding skills I would grab the source and change the algorithm myself. But Alas, I have proven to be a really bad coder.

I suppose it boils down to my preference for meaningful references in the config files I screwup^H^H^H^H^H^H^H edit.

Am I asking too much? Most likely, I usually do.;)


Randall.

---

### Post by 23meg on 2006-11-24
> **rcrook said:**
> That's fine but my question still stands, why a hash and not a descriptive ID? Characters are just hex codes too. Would it be so hard to replace the algorithm that generates the hash with code that allows for a human readable ID to be made and used? Seriously, I don't see why we should be to lazy to try and keep a file format convention "fstab" (which has been around for a lot longer than ext3) just because its easier to knock up a hash generation algorithm than it is to write some code that generates a descriptive id.There isn't one single method but various methods for generating a UUID, some relying on randomness and known hash algorithms, some on computer specifics such as the MAC address. For example with early UUIDs it's very easy to extract the time they were created from the string. UUIDs aren't specific to filesystems; they can be used to uniquely identify anything, so the "problem" lies deeper than the level of filesystems.

Sure, a UUID in its current form isn't strictly required to be present in the fstab file, since nobody will ever want to attach and swap a trillion drives to their system, but having a more elegant identifier in its place would mean writing this identifier somewhere on each volume at install time and then relying on it afterwards, which perhaps isn't the most technically elegant solution. The UUID, however, is guaranteed to be present at install time and its use requires no modifications to the volume. There are probably other reasons why the aesthetic elegance of an identifier is inversely proportional to the technical elegance of its applications.

---

### Post by argie on 2006-11-25
Just run "blkid" and it'll list all the filesystems and their UUIDs anyway.

---

