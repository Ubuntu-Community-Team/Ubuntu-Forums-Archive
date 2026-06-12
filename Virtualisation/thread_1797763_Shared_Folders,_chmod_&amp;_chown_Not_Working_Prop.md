---
title: "Shared Folders, chmod &amp; chown Not Working Properly Virtualbox"
date: 2011-07-05
forum: Virtualisation
---

### Post by derekeverett on 2011-07-05
Hey all,

I bought a new computer a couple weeks ago.. I'm back on the mac after running an HP box for the last couple years. I have installed Ubuntu 11.04 using virtualbox. This is a process I've gone through many times on many machines. Mounting shared folders is not new to me.

The installation went fine. I checked MD5 sum and everything was perfect. The Guest Additions also installed with no problems.

I was able to create 4 shared folders in the VM. I called them simply mac_music, mac_documents, mac_pictures, and mac_movies. Made them permanent machine shared folders. Just like I've done 100 times before. So far so good.

Here's my first issue.. I can mkdir to make a mount directory no problem.. but the owner shows as root everytime. Even if I do it in my home folder. And I can't sudo chown to change it to save my life. I get no error in the terminal.. the change simply doesn't take effect.

So obviously chmod isn't working either.. and I can't get access to these directories.

I modified the /etc/rc.local file to mount the 4 shared folders to their respective directories without a problem.. but only the music folder seems to mount properly. I can access that one.. despite not being the owner of the directory. But the other directories have me locked out so I can't tell if it's working or not.

I changed into root user to try and change ownership of the directories.. and no luck.. again I get no error in the terminal.. the change simply does not occur.

Any thoughts??

Thanks.

---

### Post by CharlesA on 2011-07-05
What file system are the folders residing on?

---

### Post by derekeverett on 2011-07-05
> **CharlesA said:**
> What file system are the folders residing on?

They live on my Mac hard drive. So it would be the standard Mac OS Journaled file system.

---

### Post by Morbius1 on 2011-07-05
I'm confused.

Is the host OSX and the guest Ubuntu?

If you shared the folder within the VBox application there was no need to manually mount them in the VBox guest. They are automatically mounted at :

[COLOR=Blue] /media/sf_[I]something

[/I][COLOR=Black]**EDIT**: And they should have mounted with owner = root, group = vboxsf, and permissions of 0770.[/COLOR][/COLOR]

---

### Post by derekeverett on 2011-07-05
> **Morbius1 said:**
> I'm confused.

Is the host OSX and the guest Ubuntu?

If you shared the folder within the VBox application there was no need to manually mount them in the VBox guest. They are automatically mounted at :

[COLOR=Blue] /media/sf_[I]something

[/I][COLOR=Black]**EDIT**: And they should have mounted with owner = root, group = vboxsf, and permissions of 0770.[/COLOR][/COLOR]

Yes OS X is host.

I am not in the habit of selecting "auto-mount" when I create the shared folders with the VM. So I hadn't been selecting that option.

After reading your post I created one that way. Your right it does auto-mount to the /media directory as sf_Filename. However I still can't access it.

---

### Post by Morbius1 on 2011-07-05
Maybe you aren't a member of the group:
```
 sudo gpasswd -a your-user-name vboxsf
```Then logoff from the guest and login again so that the group membership change takes affect.

---

### Post by derekeverett on 2011-07-05
Thanks everybody for your assistance. I have determined that something, although I have no idea what, has gone really wrong here.

I am now getting error messages in the terminal for trying standard commands and I am having trouble accessing random folders. Also, all my applications, every one of them, seem to have disappeared from the applications directory on the Unity desktop.

As this was a new installation, it's easier for me to just wipe this one out and re-install then try to repair this degenerating mess.

Sometimes that is your answer...

Thanks again.

---

### Post by derekeverett on 2011-07-06
> **Morbius1 said:**
> Maybe you aren't a member of the group:
```
 sudo gpasswd -a your-user-name vboxsf
```Then logoff from the guest and login again so that the group membership change takes affect.

For anybody else having these problems.. Moribus was right also, for whatever reason I was not a part of the vboxsf group.

I have re-installed in the VM and all works now. I actually set-up the shared folders in Virtualbox and set them to auto-mount BEFORE I installed Ubuntu in the VM.

After adding the guest additions, the shared folders appeared in /media directory but I was again unable to access them.

I just added my name to the group in /etc/groups and re-booted and now all is just peachy. With only 1 user on the system you would figure it would just add me to the group.. but it doesn't appear to do that by default.

---

### Post by rhigmus on 2011-09-13
> **CharlesA said:**
> What file system are the folders residing on?

Thanks much for that! I was having a similar problem with chmod and chown. I realised reading your comment that the files I wanted to change resided on an NTFS partition I share with a windows os install.

Thanks!

---

