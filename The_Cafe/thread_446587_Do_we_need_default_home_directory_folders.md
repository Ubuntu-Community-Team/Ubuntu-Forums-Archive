---
title: "Do we need default home directory folders?"
date: 2007-05-17
forum: The Cafe
---

### Post by tehkain on 2007-05-17
I have been thinking about this for a while now. I do not look to copy implementations from other OSes but when they are right - they are right. One thing I have noticed that is missing in ubuntu is a default set of folders within your home directory. OS-X has the Movies, documents, pictures, and music folders. Windows has the My Pictures folders(and others). I can easily create these folders but I think ubuntu would do well to create a few by default.

When a new user goes to save an item he can select the directory and not have to create a directory. Having these basic folders upon install allows super new people to better organized and less cluttered.

Another thing I would like is smart folders. Like the Trash: folder but for Music or Images. So when you enter the image folder a new bar pops down with a button to start a slideshow or something like that. Or the Document folder would have a special document viewer inside of nautilus. Is there any implementation like this in the linux world?

---

### Post by Tomosaur on 2007-05-17
> **tehkain said:**
> I have been thinking about this for a while now. I do not look to copy implementations from other OSes but when they are right - they are right. One thing I have noticed that is missing in ubuntu is a default set of folders within your home directory. OS-X has the Movies, documents, pictures, and music folders. Windows has the My Pictures folders(and others). I can easily create these folders but I think ubuntu would do well to create a few by default.

When a new user goes to save an item he can select the directory and not have to create a directory. Having these basic folders upon install allows super new people to better organized and less cluttered.

Another thing I would like is smart folders. Like the Trash: folder but for Music or Images. So when you enter the image folder a new bar pops down with a button to start a slideshow or something like that. Or the Document folder would have a special document viewer inside of nautilus. Is there any implementation like this in the linux world?

I personally just make my own folders - documents, music, programs (that I don't want to install system wide) etc. While I'm not objected to the idea, I just think people will end up organising things however they feel like anyway. 

I definately agree with the 'smart folders' idea though, it'd be a great feature.

---

### Post by flowingfire on 2007-05-17
You know, I created a "My Documents" folder in my home directory.  Do you know what Feisty did?  I'm not sure of this was the work of the Feisty gods or the work of Wine or what... But it automatically created "My Photos" "My Music" and other such folders.

Hmm..... Where did these come from oh mighty Ubuntu?!!! Where!  oh WhERE?

---

### Post by Tomosaur on 2007-05-17
> **flowingfire said:**
> You know, I created a "My Documents" folder in my home directory.  Do you know what Feisty did?  I'm not sure of this was the work of the Feisty gods or the work of Wine or what... But it automatically created "My Photos" "My Music" and other such folders.

Hmm..... Where did these come from oh mighty Ubuntu?!!! Where!  oh WhERE?

If you installed Ubuntu over Windows - it has the ability to migrate your 'My Documents' folders from Windows.

---

### Post by bastiegast on 2007-05-17
> **Tomosaur said:**
> I personally just make my own folders - documents, music, programs (that I don't want to install system wide) etc. While I'm not objected to the idea, I just think people will end up organising things however they feel like anyway. 

I definately agree with the 'smart folders' idea though, it'd be a great feature.

That's not the point, you can always organize your files the way you want, but its just easy when saving files when there's a default set of folders you can select from the left(like home folder and disk drives now).

---

### Post by Tomosaur on 2007-05-17
> **bastiegast said:**
> That's not the point, you can always organize your files the way you want, but its just easy when saving files when there's a default set of folders you can select from the left(like home folder and disk drives now).

I wasn't making a 'point', I was just saying - I don't think it's something we should worry about, since most people will do whatever they feel like anyway. The normal 'My Documents' directories in Windows don't provide everything I need, and don't meet the structure that I like to use. The home directory is already akin to the 'My Documents' directory, and from there its just up to the user.

In any case, like I said, I'm not objecting to it - but the likelihood is that I'll just wipe the 'default' setup anyway and create my own, which is suited to my own needs.

---

### Post by pmj on 2007-05-17
I can't imagine that those media folders serve the needs of anyone, except perhaps places to temporarily dump things you save from your web browser and so on. As soon as you have more than a hundred files you really can't use the media folders anymore.

Also, I have a feeling that Nautilus will never support the smart folders thing. Not only would it be doing the job of other applications (image viewer etc), but Nautilus is too slow and bloated already, and development seems to move at a snail's pace.

---

### Post by bastiegast on 2007-05-17
I would use them, I used the documents folder on back on SuSe, I have a documents folder in my home dir and would love to be able to select it from the menu from the left(which undoubtly is possible now but requires tweaking). I know lots of friends who use the my pictures and my videos folders.

So they serve need for me and probably others too.

---

### Post by tageiru on 2007-05-17
[http://www.freedesktop.org/wiki/Software/xdg-user-dirs](http://www.freedesktop.org/wiki/Software/xdg-user-dirs)

Fedora is using it and I expect Ubuntu to follow.

---

### Post by Dragonbite on 2007-05-17
If I have a category I want usable by everybody on the system, I make a directory off of the **/home/** directory (such as **/home/music/**) and symlink it into my Home directory.

Otherwise, I just make them myself, usually without the "My " because the space messes things up a little when using the command line ... I keep forgetting to put " " around the directory name.

At the same time, if I want to save all of my files, I back up **/home/*** and it gives me everything from all users.

---

### Post by forrestcupp on 2007-05-17
I think Windows has way too many default folders.  But, yes, it would be nice if Ubuntu had a few of the necessary ones by default.  Creating all of my folders was one of the things I had to do when I installed.

---

### Post by jonallport on 2007-05-17
I've just had a look through /usr/sbin/adduser with a view to inserting a command to make these folders when, lo and behold:  when creating a home directory it will copy the contents of /etc/skel to it and set ownership/permissions for the owner of the home directory.

Have just tried it and it works!

Is this of any help?

---

### Post by ablaze on 2007-05-17
Okay, I tend to love Macs, so I feel a bit biased, but it generally is a good thing to seperate different kinds of media and to give a novice user a predefined possibility to do so. 

I love Apple's solution: Music, Pictures, Documents, Movies, Public, Desktop, and Websites.

If these would be available on all Ubuntu user accounts, they could also be better integrated in the system. If you can assume a Music folder exists, all apps could put their stuff in a subdirectory of it, or you could add some kind of media browser based on the folder structure for different apps (like in the iApps on the Mac).

---

### Post by brim4brim on 2007-05-17
I don't think so.  The naming convention for these folders will cause problems.  Everyone is going to have to learn to create a folder at some point.  A lot of people get irritated by default folders names especially windows My * convention which is just stupid.  I know they are my documents, they are in my profile.

---

### Post by karellen on 2007-05-17
> **tehkain said:**
> I have been thinking about this for a while now. I do not look to copy implementations from other OSes but when they are right - they are right. One thing I have noticed that is missing in ubuntu is a default set of folders within your home directory. OS-X has the Movies, documents, pictures, and music folders. Windows has the My Pictures folders(and others). I can easily create these folders but I think ubuntu would do well to create a few by default.

When a new user goes to save an item he can select the directory and not have to create a directory. Having these basic folders upon install allows super new people to better organized and less cluttered.

Another thing I would like is smart folders. Like the Trash: folder but for Music or Images. So when you enter the image folder a new bar pops down with a button to start a slideshow or something like that. Or the Document folder would have a special document viewer inside of nautilus. Is there any implementation like this in the linux world?

indeed, it's very difficult for the new user to make news folders. such a daring task...
I hate those default folders, the first thing I do is to replace them with my own folders

---

### Post by forrestcupp on 2007-05-17
> **brim4brim said:**
> I don't think so.  The naming convention for these folders will cause problems.  Everyone is going to have to learn to create a folder at some point.  A lot of people get irritated by default folders names especially windows My * convention which is just stupid.  I know they are my documents, they are in my profile.

That's why MS got rid of the "My" in their Vista folders.

---

### Post by heimo on 2007-05-17
> **forrestcupp said:**
> That's why MS got rid of the "My" in their Vista folders.

I thought they removed "My" prefix because those files no longer belong to you under Vista?

---

### Post by Bou on 2007-05-17
> **tehkain said:**
> I have been thinking about this for a while now. I do not look to copy implementations from other OSes but when they are right - they are right. One thing I have noticed that is missing in ubuntu is a default set of folders within your home directory. OS-X has the Movies, documents, pictures, and music folders. Windows has the My Pictures folders(and others). I can easily create these folders but I think ubuntu would do well to create a few by default.

When a new user goes to save an item he can select the directory and not have to create a directory. Having these basic folders upon install allows super new people to better organized and less cluttered.

Another thing I would like is smart folders. Like the Trash: folder but for Music or Images. So when you enter the image folder a new bar pops down with a button to start a slideshow or something like that. Or the Document folder would have a special document viewer inside of nautilus. Is there any implementation like this in the linux world?

That'd be fine as long as the folder's names would be automatically translated to the system's language. I for one don't want to save my music in ~/My Music, I want it in ~/música.

---

### Post by foresth on 2007-05-17
Seriously, does really **anyone** use this pre-created folders?

---

### Post by ixus_123 on 2007-05-17
I for one wouldn't like any more folders in the home folder.

If I want them I'll make my own. It would annoy me to get an install of Ubuntu and them have to go about removing things.

---

### Post by tehkain on 2007-05-17
> **foresth said:**
> Seriously, does really **anyone** use this pre-created folders?
There are no precreated folders so no one uses them. If you are talking about osx then yes many people do.

> **ixus_123 said:**
> I for one wouldn't like any more folders in the home folder.

If I want them I'll make my own. It would annoy me to get an install of Ubuntu and them have to go about removing things.

I do not like that there are tons of packages included in ubuntu-desktop that I do not want. I remove them and it doesnt bother me. Look this is something for a new user. If you ever had to deal with someone who is computer stupid you should know that if they arnt given folders from the start everything ends up sitting in a slue of 'New folder 1-1million'. 

As for smart folders, I do not think they will make nautilus any heavier. Since it already can play music files and display images. It would just take up the bar where the Trash: page has the 'empty trash' button.

---

### Post by aysiu on 2007-05-17
I think it'd be an interesting experiment.

What annoyed me about those folders in Windows wasn't there existence but their automatic re-creation after deletion; for example, if I don't have any eBooks, I don't want a My eBooks folder.

What annoyed me about the predefined folders in Mepis was how many of them there were (more than just a few).

A simple Documents, Music, Pictures would probably do the trick--one of the few things OS X gets right.

---

