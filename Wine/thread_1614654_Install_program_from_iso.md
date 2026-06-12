---
title: "Install program from iso"
date: 2010-11-05
forum: Wine
---

### Post by beew on 2010-11-05
So what is the procedure to install a program in wine from one or several isos?

No, I don't want to burn any CD. Thanks.

---

### Post by msakms on 2010-11-05
[FONT=Comic Sans MS][SIZE=2][COLOR=Navy]First, you need some software to mount your iso images. I use "Furius iso Mount", there are bunch of other tools like "Acetone" and many others. Find those tools using Synaptics package manager and mount your iso image.
 After that browse to your .exe file---->right click and choose properties----->Permissions----> make sure you mark "Allow executing file as program" [/COLOR][/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
Now you can open the .exe file with wine and carry on the installation procedure just like you do on windows. 
Cheers[/SIZE][/FONT]

---

### Post by cwwilson721 on 2010-11-05
> **msakms said:**
> [COLOR="Red"]First, you need some software to mount your iso images.[/COLOR] I use "Furius iso Mount", there are bunch of other tools like "Acetone" and many others. Find those tools using Synaptics package manager and mount your iso image.
 After that browse to your .exe file---->right click and choose properties----->Permissions----> make sure you mark "Allow executing file as program" 
Now you can open the .exe file with wine and carry on the installation procedure just like you do on windows. 
CheersActually, No, you DON'T NEED a program to do so. but it is CONVIENIENT

```
sudo mkdir /mount/<ISONAME>
mount -o loop <FOO>.iso /mnt/<ISONAME>
```
<ISONAME>=Whatever you want it to be
<FOO>= name of iso

Why complicate matters?

---

### Post by beew on 2010-11-07
Hi, 

Thanks for the reply. 

I actually thought about mounting iso just like I would in installing Linux program. But to do that using tools lilke furius iso apparently does not work because you need to have root privilege to run the installer and you need to know the directory in which the iso is mounted (so you can access the installer on the terminal) 

So basically I use cwwilsion721's method to install Linux programs that are in isos. (the command line) , but my problem here is that I think using sudo in connection with WINE is kind of a bad idea, or maybe it doesn't matter if it is just to create a mount point?

---

### Post by thatguruguy on 2010-11-08
You're not using sudo in connection with Wine, you're just using it to mount the iso.

---

### Post by cwwilson721 on 2010-11-08
And THEN, after you have mounted the iso, use winecfg to point the cd to the iso.

Ex:
```
In the 'Drive' tab...
ADD
Select Drive Letter
OK
Then in 'Path', type in where the iso is, or click 'Browse'
(Make sure the Drive you created previously is still selected)
OK

```

Pretty straightforward process...

---

### Post by oldgraf on 2010-11-09
Is there another way to mount .iso ? M[COLOR=#000000]y kids have their non root account and I agree they can  install things in wine [/COLOR]without my intervention

---

### Post by I'mGeorge on 2010-11-10
well you don't really have to mount the iso file, you can just extract it with file-roller archiver or you can view it I believe with midnight commander the norton commander version for linux.

---

