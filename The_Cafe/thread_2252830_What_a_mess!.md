---
title: "What a mess!"
date: 2014-11-15
forum: The Cafe
---

### Post by mikodo on 2014-11-15
I admire organized people. I wish I was one.

 I'm amalgamating two 'buntu's. Both had there own /home partitions. There's stuff everywhere. I am constantly looking all over the place to check if data is duplicated, before putting it on an external drive, in preparation of installing the Data all in one place, on a new drive. I can't find anything quickly.

I need an e-organizer! Some "Magic Jeannie". 

This is just like my offices, too! I hate mundane filling and cleaning up. I pay for it in lost time and frustration, while looking for things.

YUK!

---

### Post by Roasted on 2014-11-15
Perhaps fire up a centralized file server to store everything and work from that? I use my multiple systems for different tasks, but there are some things I want to be consistent between all systems. I let my dual screen desktop do bigger tasks, my laptop do more mobile tasks, etc. But it all stems back to my server. 100% of my pictures are stored on the server. All music stored on server. All document type files are synchronized between my devices from my server using ownCloud. It takes a lot of the guess work out of the game when you know your server is

1) the central point of contact for all pictures
2) the central point of contact for all music
3) the decentralized point of contact for all documents that will sync the documents in question to all systems

Of course, it takes work and a lot of reorganization on your part to get to this point, but once it's done, it's pretty gravy. :)

---

### Post by mikodo on 2014-11-15
> **Roasted said:**
> Perhaps fire up a centralized file server to store everything and work from that? I use my multiple systems for different tasks, but there are some things I want to be consistent between all systems. I let my dual screen desktop do bigger tasks, my laptop do more mobile tasks, etc. But it all stems back to my server. 100% of my pictures are stored on the server. All music stored on server. All document type files are synchronized between my devices from my server using ownCloud. It takes a lot of the guess work out of the game when you know your server is

1) the central point of contact for all pictures
2) the central point of contact for all music
3) the decentralized point of contact for all documents that will sync the documents in question to all systems

Of course, it takes work and a lot of reorganization on your part to get to this point, but once it's done, it's pretty gravy. :)
Sounds great. For you.

I am an older casual noober, so the best I can do is put all my stuff on a partition on my only computer and symb-link it to my installs.

I forgot to say thanks! ;)

---

### Post by Roasted on 2014-11-15
Understandable. It's worth mentioning that if you do get curious about a more automated process, you're in the right place to ask some questions if you find yourself interested. I'd be more than happy to help wherever possible. :)

---

### Post by sammiev on 2014-11-15
> **Roasted said:**
> Perhaps fire up a centralized file server to store everything and work from that? I use my multiple systems for different tasks, but there are some things I want to be consistent between all systems. I let my dual screen desktop do bigger tasks, my laptop do more mobile tasks, etc. But it all stems back to my server. 100% of my pictures are stored on the server. All music stored on server. All document type files are synchronized between my devices from my server using ownCloud. It takes a lot of the guess work out of the game when you know your server is

1) the central point of contact for all pictures
2) the central point of contact for all music
3) the decentralized point of contact for all documents that will sync the documents in question to all systems

Of course, it takes work and a lot of reorganization on your part to get to this point, but once it's done, it's pretty gravy. :)

When I retire this will be the first thing I do.

---

### Post by QIII on 2014-11-15
I just buy a bunch of computers, install a distro on each, have one as my server for all the stuff I want to have available to all of them and use one computer as my primary to remote to all the others with NoMachine.

With the 5 computers under my desk, my laptop and 5 more scattered around the house, I can just sit my fat behind in my comfy chair and play around all I want.

Admittedly, this is a lot easier if your wife owns a business and makes a lot more money than you do.

:)

---

### Post by bashiergui on 2014-11-16
That's what scripting is for. You could write a simple bash script to recursively move files to the new location. Have it check extensions so that .jpgs go into /NewDrive/Photos and .pdfs go into /NewDrive/Documents, etc. You can have it check the hash of each file being moved against everything already there, and if there are matches (ie duplicates) move it to /dev/null instead.

---

### Post by frankmorris2 on 2014-11-17
Hello,

I use the program fdupes (sudo apt-get install fdupes) to find all the duplicated files before an operation like this.

It produces a list of duplicated files. You can also specify an option to delete the duplicates and keep only one file.

Have a nice day.

---

### Post by mikodo on 2014-11-17
Thank you, for thinking about this and your suggestions!

> **bashiergui said:**
> That's what scripting is for. You could write a simple bash script to recursively move files to the new location. Have it check extensions so that .jpgs go into /NewDrive/Photos and .pdfs go into /NewDrive/Documents, etc. You can have it check the hash of each file being moved against everything already there, and if there are matches (ie duplicates) move it to /dev/null instead.
This looks so nice but, writing scripts are above me. I will probably use an app for this.

> **frankmorris2 said:**
> snippet

I use the program fdupes (sudo apt-get install fdupes) to find all the duplicated files before an operation like this.

It produces a list of duplicated files. You can also specify an option to delete the duplicates and keep only one file.
I have started reading about fdupes, especially since you have used it and have been happy with it.

While following links and reading about fdupes, I also found a GUI app, to do this too, [FSlint.]("http://en.flossmanuals.net/fslint/") Like fdupes, it is in the repos. I will use one of them.

Regards.

---

