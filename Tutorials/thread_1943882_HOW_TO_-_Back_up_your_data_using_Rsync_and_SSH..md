---
title: "HOW TO - Back up your data using Rsync and SSH."
date: 2012-03-20
forum: Tutorials
---

### Post by Roasted on 2012-03-20
(scroll to bottom if you want a much less informative synopsis of what will be covered)

When I first began tinkering with this idea, the whole SSH thing kind of confused me, mostly because I didn't think SSH would be easy for an end user to utilize. While SSH is very complex in design, they've made it super easy for the end user to set up an authentication key set. Essentially, SSH is a 1 to 1 authenticated connection that can be obtained without a password. Once this is in place, you can utilize rsync to run automatically.

Before we begin, please ensure you have openssh-server installed on your file server in question.
```
sudo apt-get install openssh-server
```

Next, we need to set up a key pair. You will receive a public key and private key. 
```
ssh-keygen
```

You will be asked some questions, such as whether or not you want a password to the key pair, etc. I chose no and basically left everything else default. I went with no password because SSH keys are pretty darn secure, and plus I wanted this to be automated. I was not sure how I could automate this process while still having a password on it.

The public key needs to get copied to the authorized_keys file on the server. Thanks to a handy command, this is painless. Replace jason@192.168.1.150 with what your setup would be.
```
ssh-copy-id jason@192.168.1.150
```

It'll ask you for your password. Put in your password to the user account you're authenticating against on the file server. Once done, you should be able to run:
```
ssh jason@192.168.1.150
```

If it did not ask for a password and your prompt changed, you're good to go. If it asked you for a password, something is likely off. Please note, if you mess around with the SSH keys (by deleting them, adding new ones, etc.) it'll require a reboot (some people have told me log out + log in works fine too) to reset. I don't know enough about that to explain what's happening besides taking the educated guess that the SSH key is getting locked to your session. Unless you plan to tinker around like I did, where I would delete the SSH keys and re-generate them over and over for learning purposes, you won't run into this issue. But if you do, I wanted to throw this out there.

So, SSH is set up and you're good to go. Now what? It's rsync's turn. You have opened the door with SSH, now you need to put it in gear with rsync. Rsync is a remote synchronization tool. For my uses, it's pretty much awesome. I suggest you folks read the rsync man page for more information. Just a side note, anybody reading this who uses Linux, please keep man pages in mind. They're quicker than Google. Honestly. You can read them up by going to terminal and typing "man rsync". Of course, you can substitute rsync for any other command to read more about it as well, aka "man cp" etc.

The man page will go over the functionality of a bunch of flags. There's a few I personally use and I'll cover them in my own words below.

-a    Archive mode. This keeps the time, permissions, owner, group, and other various settings the same as the source. I like using -a because it ensures that my data on the file server match my data on the desktop, even down to who owns what and the time stamps.

-z    Compression mode. I haven't really used this until recently. I'm not sure if I notice a difference because rsync is pretty fast to begin with, but I tack it in there, mostly because, why not?

--exclude=    Exclude mode. This is if you want to exclude a specific directory, trash, videos, etc. For example, let's say you want to exclude ALL hidden files/folder... you would do --exclude=.* Notice after the equals sign there is a period and *? That ensures you're doing the wild card, meaning EVERYTHING, but only after the period. Since hidden files/folders are began with a period, you can see how it would include .folder1 .folder2 .folder3, etc. 

**Note -** Personally, I would definitely recommend excluding .gvfs. .gvfs is the gnome virtual file system. It essentially acts as a mount point for network resources. Let's say your file server is accessible through .gvfs. If you rsync everything and don't exclude .gvfs, you're in essence duplicating the data on your file server that already exists, because it'll exist in its primary folder, as well as through .gvfs thanks to your file server.

/home/jason/Documents
/home/jason/Music
/home/jason/Pictures
/home/jason/.gvfs/Documents
/home/jason/.gvfs/Music
/home/jason/.gvfs/Pictures

By excluding .gvfs, you avoid this all together. If you're backing up a home directory, I'd suggest doing it. Using simply --exclude=.gvfs works for me, but if you need the full path, it would of course be --exclude=/home/jason/.gvfs

--delete    This will delete files on the destination that don't exist on the source. Let's say you have a folder that contains 100 GB of data and it's simply named "data". If you rename it to "data2", your server would contain a copy of data and data2 @ a grand total of 200 GB. If you want the data on your server to be identical, use --delete. If you want to have some sort of "older file redundancy" (I know some people prefer this), don't use --delete.

--progress    If you run rsync manually, you'll be able to see the progress of what's going on instead of just a flashing cursor. I only use this flag if I want to run the command manually and see what it's doing. I don't bother using this when it's "showtime" and I want it automated in the background.

Other than that, it's just about setting up the source and destination. Let's start with the destination, since after all, we're tinkering with SSH here so it's a tad bit different. For the destination, you'll need the user, server, and folder path. As I said, my name is Jason, and my file server is 192.168.1.150. My folder path on my server in particular is /media/NAS/jason. In my case, NAS is a network drive I shared out, so it's pretty specific to my situation. Yours is likely to differ. Tailor the destination to your own situation. If your "backup drive" is /media/storage and you have a folder on storage named frank, then use /media/storage/frank, etc. In my case:
```
jason@192.168.1.150:/media/NAS/jason
``` is my destination.

Now, about the sources. They're simple enough, as it's the same as above except it doesn't include user@server. 

If you want your entire home directory to be synchronized, you can do so with just:
```
rsync -az /home/jason jason@192.168.1.150:/media/NAS/jason
```

If you want your entire home directory synchronized but with the exclusion of .gvfs and the --delete flag, use:
```
rsync -az --exclude=.gvfs --delete /home/jason jason@192.168.1.150:/media/NAS/jason
```

Getting the jist of it now? 

Note, you can have multiple sources as well, which makes it handy if you only want to back up a few specific folders to your file server. In my case, I had limited file server space, so I only wanted to back up the most important data to my file server, which to me is Documents and Pictures. Example:
```
rsync -az --exclude=.gvfs --delete /home/jason/Pictures /home/jason/Documents jason@192.168.1.150:/media/NAS/jason
```

You can then set up a Cron job for this to run at specific times. I never run rsync as root, so when I set it up in Cron I set it to launch as jason and just tagged the above rsync command in.

I've since moved away from the Cron route. I shut down my computer at night, but my file server stays up all the time, I added an entry in "Startup Applications" to do the backup for me, which is handy because it runs at system startup. I named it NAS Backup and put the above command in the command field. Everything works like a charm with zero input needed from me. :guitar:

Quick tip, if you'd like to check out a decent rsync GUI, fire up grsync. It's easy to use and will help you structure out the rsync command if you're not entirely sure just yet. Just note, there is no --exclude= flag in the GUI, so you'll have to add it manually under Additional Options, but that's pretty darn easy to do. Grsync also doesn't use -a, but instead it breaks up -a to -t -o -p -g etc. Read the rsync man page under the -a section to see why this makes little/no difference.

Once you have it formulated the way you want, you can also do a test run, which is one of the features of grsync to make sure it works properly prior to giving it the green light. Assuming all is well and you're done, you can schedule this grsync job with, you guessed it, either Startup Applications or Cron. Keep in mind, the syntax for it is "grsync -e jobname". So if you named the job "backup", you'd run grsync -e backup. This would be the same for Cron or Startup Applications.

I tested it running it in Startup Applications. It comes up with a GUI window when I log in showing me the status of the data transfer. If I go the route with Startup Applications and just throwing the full rsync command in, it does it completely in the background. Depending on how much of a visual status you want may dictate which route you go.

At any rate, serious kudos to the SSH, Rsync, and Grsync team, as they've brewed up some very impressive technologies here.

**Summary**

The above was meant to be super informative. I hope some users can set up a backup system that works for them. Keep in mind, you never know when Mr. HardDrive is going to tank on you, so plan ahead. Below is a rough summary of what you're doing for the users who don't want to read through a mountain of text. Note: Change the below settings to match your setup, unless your name happens to be Jason and your file server happens to be 192.168.1.150.

**Server **
```
sudo apt-get install openssh-server
```

**Client** 
```
ssh-keygen
```

**Client **
```
ssh-copy-id jason@192.168.1.150
```

**Client **
"Startup Applications" - Select New - Name it backup or whatever you please, and add desired rsync line in the command box, such as:
```
rsync -az --exclude=.gvfs --delete /home/jason jason@192.168.1.150:/media/NAS/jason
```

---

### Post by zeefreak on 2013-01-22
i've been using rsync and ubuntu for years and i've run into something i can't explain. perhaps you might know the answer:

i've recently got a new backup solution, a synology ds713+. i'm trying to connect to it via rsync. currently, i'm rsyncing to an ubuntu server, and it just works. the synology keeps throwing errors, and when i google around to figure out what is up, it looks like i need to set up an rsync daemon and put a plaintext password in a secrets file.

here is where i'm confused. i've never done that on my ubuntu server. rsyncd isn't even running. as you've done in your documentation here, the only thing i've done is sent a public key over to the server to avoid typing the password.

further research into the problem says that you can tunnel rsync through ssh with '-e ssh' switch.

again, confusion. my rsync seems to do this by default without that switch.

it seems somehow that the ubuntu [and bsd, where i grew up] implementations of rsync automagically use ssh, only i can't actually find anything that says this.

it's obvious to me that i'm missing something, but i really can't figure out what it is.

little help?

---

### Post by Roasted on 2013-01-23
I understand that originally rsync was not based on SSH, which is why tunneling through SSH was a popular method. If you look on Google, any areas that suggest this are likely to be dated back quite a few years. Newer implementations of rsync have utilized SSH by default which negates the need to put that into the command. It is pretty convenient that by simply changing the destination dictates how it will operate. For example, if I rsync -a /media/storage /media/storage_II, I'm working local, but if I rsync -a /media/storage roasted@192.168.1.10:/media/storage_II, I'm working over SSH (pending that SSH keys are set up of course).

I'm a little unfamiliar with the unit you're rsyncing with, but I've at least heard the Synology name quite a lot. Is this unit running some sort of Linux based operating system? I ask this because I always thought rsync was integrated with every Linux distro out there, until recently where I fired up Raspbian Linux on my Raspberry Pi. I found out that rsync was not on the default image, so I had to run an apt-get install rsync first before I could actually utilize rsync in the way I wanted. 

*Raspbian Linux is based on Debian, hence the apt-get install correlation. 

Would this link be of any use by chance?

[http://forum.synology.com/wiki/index.php/Backup_Linux_desktop_data_using_rsync](http://forum.synology.com/wiki/index.php/Backup_Linux_desktop_data_using_rsync)

Let me know if you get anywhere!

---

### Post by zeefreak on 2013-01-23
roasted. thanks for your response.

the synology unit i'm using seems to be based on some linux distro, but i'm not sure what. all the query commands i have just say 'linux' i can tell that it's 64bit. it's got busybox installed on top of that.

the synology wiki page you sent is the one i've been relying on to get through this, but it's very incomplete. i'm actually planning on rewriting it when i figure it out. [yay mediawiki!]

that's also the page that got me onto this question. it outlines how to enable and set up rsyncd to get it to work. the problem is, as soon as you use rsyncd, you have to use the secrets password file where your password is plaintext. that's why i'm trying to get it to work like it does on my ubuntu boxes without the daemon so i can use ssh keys.

to make things slightly more confusing, sftp and ssh work a treat. my understanding is that if sftp and ssh work, rsync should work too since it essentially runs on top of those tools.

---

### Post by Roasted on 2013-01-23
Hmm, that is rather bizaare that you're having trouble with rsync yet SSH work. Some questions for you first... 

When you SSH into your Synology box, is there a home directory for the user you're SSHing into?

If you run rsync against your Synology box (Ubuntu-to-Synology), do you get prompted for a password, or does it just tank right then and there?

Copying SSH keys on Ubuntu (and other distros) is easy thanks to the ssh-copy-id command, but that doesn't exist in all scenarios. I've worked with some Linux distros where I had to manually copy the key over. In one instance, there wasn't a .ssh folder created for me within my home directory, so I had to create /home/jason/.ssh, set the permissions accordingly, create an authorized_keys file (set perms accordingly there as well) and then paste in the key from my client system to that file.

I'm curious if you just need to do these steps manually like I did in those scenarios.

---

