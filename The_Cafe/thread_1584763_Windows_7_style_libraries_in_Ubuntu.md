---
title: "Windows 7 style libraries in Ubuntu"
date: 2010-09-29
forum: The Cafe
---

### Post by afrowildo on 2010-09-29
This idea exists on Ubuntu Brainstorm, but has been downvoted quite considerably due to a lack of understand of the concept by the voters. This is one of the features that I've known to be a dealbreaker when people have been thinking about migrating to Ubuntu because without it it's harder to organise many folders containing similar types of data, such as the various projects you're working on for a class.

Help promote it on Ubuntu Brainstorm and bring it to the attention of the devs

[[IMG]http://brainstorm.ubuntu.com/idea/15095/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15095/)

---

### Post by demosthenese on 2010-09-29
I'm not a gnome user, but doesn't Nautilus already provide saved searches as virtual folders?

---

### Post by philinux on 2010-09-29
Moved to Cafe.

---

### Post by dv3500ea on 2010-09-29
Surely you can just use symlinks. From what I can see of the Win7 libraries, they offer nothing more than what Unix symlinks have offered for years.

Just right click on some files/folders and click 'Make Links'. For example in your ~/Music folder you could have symlinks to music from various locations.

I do think that file management can be improved (by using tags or with projects such as zeitgeist) but I don't see how these 'libraries' improve the experience on Linux, because Linux has always had similar capabilities.

---

### Post by timtom59 on 2010-09-29
Why would you want something in the style of windows...? Im not normally a biast person however when it comes down to windows i hate it...

---

### Post by Tibuda on 2010-09-29
> **timtom59 said:**
> Why would you want something in the style of windows...? Im not normally a biast person however when it comes down to windows i hate it...
because it is a good feature.

---

### Post by afrowildo on 2010-09-29
@dv3500ea Creating symlinks isn't exactly the most user friendly experience in the world and when you have them, you only have a folder full of links which you can only access one at a time, whereas with Windows 7 libraries, the included folders are in a collapsable arrangement that give you easy access to any number of them simultaneously without having to open multiple windows/tabs.

@timtom59 Why is a feature implemented in Windows a bad thing? You realise that Windows got it's name because of the Windowed GUI that pretty much every desktop environment uses today.

---

### Post by Paqman on 2010-09-29
> **afrowildo said:**
> You realise that Windows got it's name because of the Windowed GUI that pretty much every desktop environment uses today.

Windows didn't actually invent that, it just implemented it well.

As glib as it seems, I think your main problem was including the word "Windows" in your Brainstorm post. Unfortunately a lot of Linux users will vote that down on principle, even if it's a really good idea that would make Linux better.

---

### Post by dv3500ea on 2010-09-29
> **afrowildo said:**
> @dv3500ea Creating symlinks isn't exactly the most user friendly experience in the world and when you have them, you only have a folder full of links which you can only access one at a time, whereas with Windows 7 libraries, the included folders are in a collapsable arrangement that give you easy access to any number of them simultaneously without having to open multiple windows/tabs.

You can symlink just the files into the folder so that it looks like just a folder full of files but these files are actually at their separate locations. When you edit/view a symlink you are actually reading/writing the original location. The only problem with this approach is when you delete a link, you don't delete the original file (which can be confusing).

If you know how to program (or are willing to learn), it shouldn't be too difficult to implement 'libraries' using symlinks. With some extra work, you could even create a nautilus plugin that improves the interface to these 'libraries'.

---

### Post by TheNosh on 2010-09-29
> **afrowildo said:**
> 
@timtom59 Why is a feature implemented in Windows a bad thing? You realise that Windows got it's name because of the Windowed GUI that pretty much every desktop environment uses today.

NLS --> Xerox --> everybody else.

---

### Post by Mr. Picklesworth on 2010-09-29
Windows has a flawed design there, I think. Well, everyone does, but Windows has implemented it completely. (All the other big desktop OSs are halfway there, but unfortunately on the same path). Libraries are a part of that implementation, and in that context they are quite clever. However, in my opinion, they are just a clever part of a bad idea.

I would call Explorer a monolithic file manager. It manages Music, Videos and Photos with special buttons and view modes for each.
For some reason that is in addition to software like Windows Media Player and Photo Gallery. That is, both Explorer and those pieces of software do the same jobs. Only the latter do it well, though; Explorer is not as good at those jobs as software actually dedicated to them. There's just a bunch of needless overlap.

And that is why I hate monolithic file managers. File managers should manage files, and only manage files. The files should never become, to the user, &#8220;photos&#8221; or &#8220;music&#8221; at this stage because that attempt at abstraction is severely limited by the fact that, at the end of a day, it's a file manager and thus forced to separate each entity according to the usual standards. (Filenames, file types, file type associations, etc.)
For something where files are an implementation detail, like a music player or a photo manager, there is a lot of freedom to present stuff in cool ways.

If the user wants Music, he should open the music player. If he wants Photos, he should open the photo manager. An ordinary user should never need to think &#8220;files.&#8221; The file manager (of the sort that can browse from / and shows every file on your system) should be a power user tool, much like a terminal.
No, we aren't there at all. But we're wasting a lot of time on this ridiculous idea that the file manager should act as a content manager. That particular idea should have died a long time ago.

---

### Post by afrowildo on 2010-09-29
> **dv3500ea said:**
> If you know how to program (or are willing to learn), it shouldn't be too difficult to implement 'libraries' using symlinks. With some extra work, you could even create a nautilus plugin that improves the interface to these 'libraries'.

Do you know what language I would need to know in order to write a nautilus plugin? I'm actually on a computing course learning C++ right now, but I've heard Python described as the unofficial language of Ubuntu.

---

### Post by Tibuda on 2010-09-29
> **afrowildo said:**
> Do you know what language I would need to know in order to write a nautilus plugin? I'm actually on a computing course learning C++ right now, but I've heard Python described as the unofficial language of Ubuntu.

The Wiki says Python or C.
[http://live.gnome.org/Nautilus/Development/Extensions](http://live.gnome.org/Nautilus/Development/Extensions)

I don't think this feature could be implemented in a plugin. Perhaps the [Nautilus-Elementary](https://launchpad.net/nautilus-elementary) developers are more willing to implement this feature than the Gnome developers.

---

### Post by Mr. Picklesworth on 2010-09-29
> **dv3500ea said:**
> You can symlink just the files into the folder so that it looks like just a folder full of files but these files are actually at their separate locations. When you edit/view a symlink you are actually reading/writing the original location. The only problem with this approach is when you delete a link, you don't delete the original file (which can be confusing).

If you know how to program (or are willing to learn), it shouldn't be too difficult to implement 'libraries' using symlinks. With some extra work, you could even create a nautilus plugin that improves the interface to these 'libraries'.

Using symlinks would probably not end well in this case. (That's A Lot of symlinks, and really we want to direct to the actual location of the files here). Check out gvfs for implementing a virtual file system :)
The gvfs-trash daemon may prove a useful example.

---

### Post by ctrlmd on 2010-09-29
> **Mr. Picklesworth said:**
> Windows has a flawed design there, I think. Well, everyone does, but Windows has implemented it completely. (All the other big desktop OSs are halfway there, but unfortunately on the same path). Libraries are a part of that implementation, and in that context they are quite clever. However, in my opinion, they are just a clever part of a bad idea.

I would call Explorer a monolithic file manager. It manages Music, Videos and Photos with special buttons and view modes for each.
For some reason that is in addition to software like Windows Media Player and Photo Gallery. That is, both Explorer and those pieces of software do the same jobs. Only the latter do it well, though; Explorer is not as good at those jobs as software actually dedicated to them. There's just a bunch of needless overlap.

And that is why I hate monolithic file managers. File managers should manage files, and only manage files. The files should never become, to the user, “photos” or “music” at this stage because that attempt at abstraction is severely limited by the fact that, at the end of a day, it's a file manager and thus forced to separate each entity according to the usual standards. (Filenames, file types, file type associations, etc.)
For something where files are an implementation detail, like a music player or a photo manager, there is a lot of freedom to present stuff in cool ways.

If the user wants Music, he should open the music player. If he wants Photos, he should open the photo manager. An ordinary user should never need to think “files.” The file manager (of the sort that can browse from / and shows every file on your system) should be a power user tool, much like a terminal.
No, we aren't there at all. But we're wasting a lot of time on this ridiculous idea that the file manager should act as a content manager. That particular idea should have died a long time ago.

actually one of the main reasons which makes me use windows is explorer 
specially on windows 7 
it give me more options than just a file manager 
and if i want to compare nautilus to explorer 

windows 7 explorer 10/10 
nautilus 0/10   
like you are comparing a bmw 2010 to some car from the 90's

---

### Post by earthpigg on 2010-09-29
if nautilus file management behaved in a way that was drastically different from the way these files and folders actually existed, i fear that i would find myself more cut off from what's actually happening with my computer.

why not just a GUI to create and manage symlinks, and leave it at that?

---

### Post by smellyman on 2010-09-29
explorer is so messy and convoluted now.  I'd prefer if they went back to the xp style

---

### Post by phrostbyte on 2010-09-29
What does Windows 7 libraries do exactly? Merge a bunch of folders together?

---

### Post by Frogs Hair on 2010-09-29
> **phrostbyte said:**
> What does Windows 7 libraries do exactly? Merge a bunch of folders together?

Pretty much , I duel boot and use both W7 and Ubuntu daily and I see no advantages in adding libraries to Ubuntu , but maybe I use my Windows file system differently than others do.

---

### Post by kreggz on 2010-09-30
I thought the reason why Windows 7 has libraries is because you put files wherever you want and the Library will pick it up.

E.g I can add a network share or a folder on the c drive and the library finds my documents.

Ubuntu uses home directories so your files shouldn't get lost in a c directory like Windows... However if you are using Network shares it can get confusing like the old Windows XP days with mapped drives.

I don't like the idea of copying Windows 7 with Libraries, but I would support an idea which makes it easier to manage your network shares directories all in your home directory. 

I think Ubuntu One and Dropbox do this but not with Samba,NFS,SSHshares where they get mounted to your desktop and Gnome menu which sucks.

---

### Post by pt123 on 2010-09-30
it already exists in Linux, just use Symbolic Links

---

### Post by julio_cortez on 2010-09-30
> **Frogs Hair said:**
> but maybe I use my Windows file system differently than others do.
Me too. I think I've never ever used libraries since I'm on Windows 7.
Probably I'm just still used to do things "the XP way", when it comes to file management.

---

### Post by CraigPaleo on 2011-01-13
There's a Nautilus extension called [Easy Union]("https://launchpad.net/nautilus-easy-unionfs").

---

### Post by disabledaccount on 2011-01-14
If someone can't handle/organize his data logically using folders and shortcuts/symlinks, then any number of more or less stupid extensions will only make things worse.
Organize your thoughts, then your data :)

---

### Post by Greytech on 2011-03-10
> **kreggz said:**
> I thought the reason why Windows 7 has libraries is because you put files wherever you want and the Library will pick it up.


I think that kreggz is the only one who has looked at Windows 7 Libraries except [afrowildo]("http://ubuntuforums.org/member.php?u=396288") .

The whole point of Libraries is to view but not keep, not only your collections in one place but perhaps others collections that are shared on the network together.

To illustrate the point, Mom may have a collection of Music that includes Modern light music, Opera, and Classical, Dad may have some Jazz and Blues son Fred has Heavy Metal and some Jazz. They all share their Music folders and Dad has his library to include all the others. He doesn't manage any but his own, Fred's folders are not always available because they are on his laptop. Most of the family Classical collection is stored on the Windows Home Server and that is always available. What the libraries allow is for anyone to include any of the shared folders in their own Library without trying to manage how anyone else wants to manage theirs.
This concept is even more powerful in business where project libraries and departmental as well as company wide libraries exist. Some may be shared R/O some as R/W many libraries will overlap but the data is not duplicated except where an individual may need to have files available when off-line.

I think what is also needed is an extension to Samba to allow Windows 7 Libraries to use central Linux storage which will include most of the NAS systems. It may be the reason that I rebuild my Linux Server as a W/Server 2008 so that the five PCs in the house can use the central storage of media and other common structures in manageable libraries.

---

### Post by MaxIBoy on 2011-03-10
> **earthpigg said:**
> if nautilus file management behaved in a way that was drastically different from the way these files and folders actually existed, i fear that i would find myself more cut off from what's actually happening with my computer.+1
This is a major complaint I have with Vista and onward.
> why not just a GUI to create and manage symlinks, and leave it at that?Actually, a better idea would be to use unionfs with loopback to merge directories *without* creating a ton of symlinks. You could implement a GUI to do this very easily.
[http://www.linuxjournal.com/article/7714](http://www.linuxjournal.com/article/7714)

---

### Post by coolen on 2011-03-20
I quite like this idea. I like to keep my files organised, but my partner's filesystem is a mess. She doesn't care.

This reflects the attitude of most people who use computers which, let's face it, is the demographic Ubuntu is going for. Sure, we geeks can keep things nice and neat, but most people don't have the time or energy. This operating system is tailored to them, not us. Fortunately, the geeks who make this operating system great have already given us almost everything that would be required to make this idea a reality.

Implementing this as symlinks would be unsatisfactory. In Greytech's (really excellent) home use case, if one person's computer is off, the symlinks will not change to reflect that. This would cause much confusion and frustration, since they would get no useful feedback.

Thus, UnionFS would make a better solution. While it doesn't allow us to add single files, it does allow us to add folders (I think that the FUSE fork would work better for this purpose, wouldn't you agree?). As many folders as we like, in fact, with a default write location for new files. If you wanted to set up some libraries for file types, this could be set to the existing directories in home.

Furthermore, there are technologies readily available which can classify a file as a document, picture, audio file, etc. (I believe Zetigeist is capable of this, or at least uses something which is). You could apply a filter to the files in any library to only show the type which is relevant.

A lot of this seems to be implemented in Easy-Union (which I cannot test right now). This would require more work to tailor that to the library's needs, and integration to make it obvious and easy.

As for the whole a-file-manager-is-a-file-manager argument, I agree, to a point, in that the file manager should not attempt to play the role of the application which handles the file. A file manager manages files, but it also helps us to work with those files, in more ways than simply moving/renaming them. Libraries allow files to be accessed in ways which are independent of their storage, both of which may be independently useful. Why force people to work with concepts they may not understand, or not wish to learn, when we can present them with other options? We already give users a recursive search option which removes them (somewhat) from the file hierarchy (but does not preserve it in any way, which is where libraries would come in).

---

### Post by Sporkman on 2011-03-20
> **Paqman said:**
> As glib as it seems...

I first read that as "as g-lib as it seems", then had to go back & correct myself.

Dork, I am...

---

### Post by PhartSmellah on 2011-07-12
This discussion is amazing - almost 30 comments and only 2 or 3 people that actually _understand_ what @afrowildo meant.

To the people that keep suggesting symlinks:
As far as I know, if I create 2 symlinks from **/home/mom/Videos** and **/home/dad/Video** somewhere else, all I get are 2 LINKS (duh...) to that folder! For the 1000th time - Libraries are not a collection of links to folders, they are an AGGREGATION of the contents of those folders.
So if **/home/mom/Videos** contains *video1.avi*, and **/home/dad/Videos** contains *video2.avi*, when I open my "library", the contents will be:
[I]video1.avi
video2.avi[/I]
And for the people suggesting to create symlinks to the actual files in the foldes / programming a plugin... c'mon. That's no solution for novice users or the average Joe that wants to install Ubuntu.
[SIZE="1"](If I'm wrong about this, please do correct me and explain how symlinks can accomplish this behavior. I've searched and can't find that it can)[/SIZE]


Now, those who think that Explorer is too bulky: that might be, but this feature is not in any way trying to add "content-exploring" features to Nautilus, by displaying photos/videos etc. On the contrary - this would be an excellent file-management improvement, just the ability to view/edit multiple folders' content directly from one location.


@CraigPaleo
Finally! Yours was the only post that addressed this feature as what it really is, and even offered a solution. I've checked the [easy-union]("http://www.webupd8.org/2010/11/display-multiple-folders-content-in-one.html") plugin and tried to use it, however I've found a few problems:
[LIST=1]
[*]The contents of the desired folders is completely united in one folder, which can lead to duplication in files/foldes. For instance, I have **~/Study/Courses/Biochemistry/** and also **~/MyFriendsStuff/Study/Biochemistry/**. In Windows, I can put both these locations in the same library, and they would still be logically (and also visually) separate. In easy-union, this would mean pulling 2 folders with the same name into one place.
[*]It works well on newly created folders, but if you try to use the Union tab on a home folder (I tried to unite a few folders into ~/Videos), it cannot be undone... some kind of bug
[/LIST]

---

### Post by del_diablo on 2011-07-12
> **Greytech said:**
> I think that kreggz is the only one who has looked at Windows 7 Libraries except [afrowildo]("http://ubuntuforums.org/member.php?u=396288") .

The whole point of Libraries is to view but not keep, not only your collections in one place but perhaps others collections that are shared on the network together.

1. When are the "tags" created?(assuming tags is need in order to actually manage the mess)
2. How can the computer separate "noise" from "music"?
3. What is needed to be done in order to actually share the music?
4. Is the "feature" really just a index over where all your socalled "music and video files" are located?

---

### Post by Npl on 2011-07-12
> **Mr. Picklesworth said:**
> Windows has a flawed design there, I think. Well, everyone does, but Windows has implemented it completely. (All the other big desktop OSs are halfway there, but unfortunately on the same path). Libraries are a part of that implementation, and in that context they are quite clever. However, in my opinion, they are just a clever part of a bad idea.

I would call Explorer a monolithic file manager. It manages Music, Videos and Photos with special buttons and view modes for each.
For some reason that is in addition to software like Windows Media Player and Photo Gallery. That is, both Explorer and those pieces of software do the same jobs. Only the latter do it well, though; Explorer is not as good at those jobs as software actually dedicated to them. There's just a bunch of needless overlap.

And that is why I hate monolithic file managers. File managers should manage files, and only manage files. The files should never become, to the user, “photos” or “music” at this stage because that attempt at abstraction is severely limited by the fact that, at the end of a day, it's a file manager and thus forced to separate each entity according to the usual standards. (Filenames, file types, file type associations, etc.)
For something where files are an implementation detail, like a music player or a photo manager, there is a lot of freedom to present stuff in cool ways.

If the user wants Music, he should open the music player. If he wants Photos, he should open the photo manager. An ordinary user should never need to think “files.” The file manager (of the sort that can browse from / and shows every file on your system) should be a power user tool, much like a terminal.
No, we aren't there at all. But we're wasting a lot of time on this ridiculous idea that the file manager should act as a content manager. That particular idea should have died a long time ago.There is a common concept below Explorer and the Media Players - and thats the [Windows Shell]("http://msdn.microsoft.com/en-us/library/dd758094(v=VS.85).aspx"). The basic idea is that you arent limited to one Media Player (from MS) handling your music, you can use any other (that implements access to the Shell libraries) and it will access your media the same way.

Again, its not implemented within Explorer, but Explorer is one of (potentially) many clients capable of accessing and managing libraries. Add a folder of file to your music library and it will automatically picked up by WMP, foobar2000 and available to networked players. Sure you could do all of this without libraries but nearly as convenient, both from a user and programmer perspective.

---

### Post by CraigPaleo on 2011-07-12
> **PhartSmellah said:**
> 


@CraigPaleo
Finally! Yours was the only post that addressed this feature as what it really is, and even offered a solution. I've checked the [easy-union]("http://www.webupd8.org/2010/11/display-multiple-folders-content-in-one.html") plugin and tried to use it, however I've found a few problems:
[LIST=1]
[*]The contents of the desired folders is completely united in one folder, which can lead to duplication in files/foldes. For instance, I have **~/Study/Courses/Biochemistry/** and also **~/MyFriendsStuff/Study/Biochemistry/**. In Windows, I can put both these locations in the same library, and they would still be logically (and also visually) separate. In easy-union, this would mean pulling 2 folders with the same name into one place.
[*]It works well on newly created folders, but if you try to use the Union tab on a home folder (I tried to unite a few folders into ~/Videos), it cannot be undone... some kind of bug
[/LIST]

Thanks. I haven't tried easy-union or Win 7. I just tried to find a solution for the OP based on what he said he wanted.  I don't see a [bug report]("https://bugs.launchpad.net/~zanko") for that bug. You might want to file one. I would do it if I used it. :)

---

### Post by alexan on 2011-07-12
It's a nice idea....



but also an obsolete idea



the modern and more realistic idea:
[https://blueprints.launchpad.net/ubuntu/+spec/tag-based-filesystem](https://blueprints.launchpad.net/ubuntu/+spec/tag-based-filesystem)

---

### Post by wrtpeeps on 2011-07-12
Librarys are probably one of my favourite features of Windows 7. 

Basically allows me now to store all my music, documents and photos in a better file structure (and all on a different partition to my Windows install) and view them all in Pictures, Music and Documents. 

Also means I can reinstall windows as much as I want without losing anything. 

Anyone on here saying they are no good has evidently never used them.

---

### Post by del_diablo on 2011-07-12
^: No, we are just running Vista.
And we are generally annoyed over that people refuse to learn to aknowledge what a file system structure is. They don't even know where they save stuff.

---

### Post by CraigPaleo on 2011-07-12
> **alexan said:**
> It's a nice idea....

but also an obsolete idea
Do you mean Win 7 libraries?  



> **alexan said:**
> the modern and more realistic idea:
[https://blueprints.launchpad.net/ubuntu/+spec/tag-based-filesystem](https://blueprints.launchpad.net/ubuntu/+spec/tag-based-filesystem)

I don't know why you'd need a new file system for that. You can already have that with Dolphin and Nepomuk. I can add as many tags as I want to a file and then find it under any of those tags. Just click on "change." 

[IMG]http://img29.imageshack.us/img29/9841/snapshot5k.png[/IMG]

Then add the tags you want. 

[IMG]http://img163.imageshack.us/img163/8274/snapshot3g.png[/IMG] 

Search for them. 

[IMG]http://img35.imageshack.us/img35/1892/snapshot4a.png[/IMG]

---

### Post by BrokenKingpin on 2011-07-12
Meh, I get by with symlinks.

---

### Post by oedipuss on 2011-07-12
I don't know if it was covered already in the union-fs suggestions, but [mhddfs]("http://romanrm.ru/en/mhddfs") sounds pretty much like what you'd want.
You just add an fstab entry like that :

mhddfs#folder1,folder2,folder3 target_folder fuse	defaults,allow_other	0	0

do a sudo mount -a, and it basically merges everything from folder1,etc to target_folder. The data isn't copied, just sort of linked. It's very transparent, you can still use the original folders normally and stuff in target_folder will be updated accordingly, plus you can easily _write to_ the target_folder, and it will choose where in the original folders to put the file, either randomly or based on free space. 
In other words, it behaves exactly like a normal folder, no special cases, no symlinks. 
I'm using it for merging two folders from separate disks and so far it has worked perfectly.

I'm not at all sure how duplicate names are handled though.. Maybe its configurable.

---

### Post by 3rdalbum on 2011-07-13
I don't mind...

...as long as the user's home directory isn't a library by default, like it is on Windows 7. It's a bit confusing to think "Well, if the home directory is a library of two or more real directories... then if I save a document to the home directory library, where exactly is it going?"

---

### Post by el_koraco on 2011-07-13
My God these Windows documentation pages are worse than the Debian wiki.

---

### Post by DerekP on 2013-01-23
> **dv3500ea said:**
> You can symlink just the files into the folder so that it looks like just a folder full of files but these files are actually at their separate locations. When you edit/view a symlink you are actually reading/writing the original location. The only problem with this approach is when you delete a link, you don't delete the original file (which can be confusing).

If you know how to program (or are willing to learn), it shouldn't be too difficult to implement 'libraries' using symlinks. With some extra work, you could even create a nautilus plugin that improves the interface to these 'libraries'.

Do you think this is a suitable alternative? It sounds like you do. Basically what you're saying is that my 73 year old dad should learn how to use symlinks, after first not knowing they exist or learn programming. Bravo solution.

---

### Post by DerekP on 2013-01-23
> **afrowildo said:**
> This idea exists on Ubuntu Brainstorm, but has been downvoted quite considerably due to a lack of understand of the concept by the voters. This is one of the features that I've known to be a dealbreaker when people have been thinking about migrating to Ubuntu because without it it's harder to organise many folders containing similar types of data, such as the various projects you're working on for a class.

Help promote it on Ubuntu Brainstorm and bring it to the attention of the devs

[[IMG]http://brainstorm.ubuntu.com/idea/15095/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15095/)

Done. For what it's worth, i voted it up.

I'm new to Linux, but i cannot find an easy, intuitive way to group my local and NAS stored files so they are easily viewable in one place. I have to start implementing 'features' that aren't on by default. I have to do research. 

Creating symlinks or edit fstab is not intuitive or as easy as Libraries in Win7. So much so i haven't tried it yet - i have to go look it up and see how to do it and what happens when i do it. Do you want people to have to research how to do something before they can do it? In Windows, it's as simple as clicking a button and then browsing for the dirs you want included in the Library (although tbh, their networked location support is not good - needs a third party app - Win7LibraryTool).

---

### Post by DerekP on 2013-01-23
> **alexan said:**
> It's a nice idea....



but also an obsolete idea



the modern and more realistic idea:
[https://blueprints.launchpad.net/ubuntu/+spec/tag-based-filesystem](https://blueprints.launchpad.net/ubuntu/+spec/tag-based-filesystem)

I see that was registered in 2007. Any progress on it or equivalent? I'm a Linux noob, and while i like Libraries in Win7 i have long thought that tagging all files is the next step... but i've not heard of any progress in any OS on this (not that i actively research it).

---

### Post by DerekP on 2013-01-23
> **disabledaccount said:**
> If someone can't handle/organize his data logically using folders and shortcuts/symlinks, then any number of more or less stupid extensions will only make things worse.
Organize your thoughts, then your data :)

So basically you're saying "do something manually, that won't produce the desired outcome, after learning how to do it that way and put up with it. Rather than do it automatically without having to learn anything". Bravo efficiency. Welcome to Linux?

---

### Post by matt_symes on 2013-01-23
Old thread.

Closed.

---

