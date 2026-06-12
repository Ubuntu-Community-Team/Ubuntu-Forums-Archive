---
title: "DVD Drives"
date: 2012-05-30
forum: Server Platforms
---

### Post by ads2996 on 2012-05-30
Hi,

I have two DVD/RW drives lieing about and i was wondering if there was any point in installing them on my server. I would be grateful in advance of any suggestions.

Thanks in Advance

---

### Post by CharlesA on 2012-05-30
I installed via USB cd drive on my server and left the regular dvd drive out of it.

I just use it as a NAS and VM host tho, so I don't have much need for a dvd drive.

It all depends on what you want to use it for.

---

### Post by ads2996 on 2012-05-30
Originally when i was considering a server i was going to use WHS. It had an add in that automatcly copied dvds when they were put in. It was called my movies. I was going to use it so I could stream my DVDs around the house

---

### Post by CharlesA on 2012-05-30
As far as I know MyMovies doesn't run on *nix, so you would have to use a different application.

I just use Samba and Windows Media Center/VLC to watch my movie library. :)

---

### Post by roelforg on 2012-05-30
> **CharlesA said:**
> I just use Samba and Windows Media Center/VLC to watch my movie library. :)
+1 (i rigged a desktop system of mine with 3 cdplayers (it runs on ubuntu server, i added a very light self-build gui setup) and shared them over samba and nfs so i could use them from my other systems)

---

### Post by ads2996 on 2012-05-30
Thank you for your advice.

---

### Post by Vegan on 2012-05-30
I have an optical drive on my server, need it to install the OS when the machine craps out.

DVD drives etc use very little power when not in use and the cost of a drive for a server is negligible I see no reason not to continue to use it.

I used that drive to also install virtual machines from operating system disks. 

Once the OS is installed I can use virtual disks, SAMBA is excellent for sharing to a Windows Hyper-V setup which is what I use. This way I can use ext4 for the Linux VMs.

In my shop virtualization is the way of the world.
:guitar:

---

