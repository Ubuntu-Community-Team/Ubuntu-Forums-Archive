---
title: "File encryption on ubuntu..."
date: 2010-07-26
forum: Security
---

### Post by FreedomOverdose on 2010-07-26
Hello

I'm really kind of paranoid about my files' security. I come from a windows environment, where I used truecrypt to encrypt the whole disk (and I provided a password at boot).

What approach should I choose with Ubuntu? I'm pretty new to linux, and I don't know what the folder hierarchy is. Should I encrypt the whole disk, or just my home directory? What exactly is stored outside and inside my home directory?  I think that the application's settings are stored on my home directory, but can there be any sensitive info outside my home dir?

Thanks

---

### Post by Bachstelze on 2010-07-26
Your home directory contains all your personal files and settings.  Whether anything else is sensitive depends on what you have put outside it, and what you consider sensitive.

For example, one does not need access to your home directory to know which programs you have installed on your system.  In some cases, you might consider this information sensitive, so you would need full disk encryption.

---

### Post by cariboo on 2010-07-26
All your configuration files, personal information and any other file you have created, modified and saved live in your home directory. As a normal user you don't have permission to files in any other directories. Encrypting your home directory should be enough.

For more info on the Linux file hierarchy, have a look [here]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html").

---

### Post by rookcifer on 2010-07-26
To be safe you should encrypt the whole disk since encrypting /home does not include swap space, which can contain information from /home.

---

### Post by FreedomOverdose on 2010-07-27
thanks for the replies guys. I'm still trying to decide whether to encrypt the whole machine or not. Is there a big difference performance-wise?

Also, I'd like to know on how files are shared in linux. I mean, there are two users, A and B. One installs a package, lets say filezilla. Some parts of filezilla are placed outside the home directory. What happens if the other user also installs filezilla?
Or once A installs filezilla (assuming he did it using sudo), it's available to every other user? If so, is there a way to restrict a package to only one user?

Thanks in advance

PS: [[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104"), thank you very much for the link. I'll definitely read every single line of it :). If there are any other linux guides that you guys think might be useful to a new linux user like me, please post :)

---

### Post by Bachstelze on 2010-07-27
> **FreedomOverdose said:**
> thanks for the replies guys. I'm still trying to decide whether to encrypt the whole machine or not. Is there a big difference performance-wise?

Depends on the hardware.  On a small netbook CPU, it might make a noticeable difference.  On a reasonably recent desktop CPU, probably not, unless you transfer a lot of data at once (e.g. a very big file from a fast medium).


> Also, I'd like to know on how files are shared in linux. I mean, there are two users, A and B. One installs a package, lets say filezilla. Some parts of filezilla are placed outside the home directory. What happens if the other user also installs filezilla?
Or once A installs filezilla (assuming he did it using sudo), it's available to every other user?

Yes.

>  If so, is there a way to restrict a package to only one user?

There's a lot of more or less convoluted ways I can think of, but no real straightforward ones.

---

### Post by FreedomOverdose on 2010-07-27
> **Bachstelze said:**
> Depends on the hardware.  On a small netbook CPU, it might make a noticeable difference.  On a reasonably recent desktop CPU, probably not, unless you transfer a lot of data at once (e.g. a very big file from a fast medium).




Yes.



There's a lot of more or less convoluted ways I can think of, but no real straightforward ones.
Ok, thanks for your reply :)

---

### Post by earthpigg on 2010-07-28
> **Bachstelze said:**
> 
> There's a lot of more or less convoluted ways I can think of, but no real straightforward ones.

There's a lot of more or less convoluted ways I can think of, but no real straightforward ones.

the least convoluted way i can think of is to see if the software in question's website offers a compressed folder for download that *doesn't* include an installer.

Iron Web Browser (fork of chromium) and the game Urban Terror are the first two things that come to mind, offering this by default. Neither comes with an installer, just a folder that you extract somewhere - including possibly somewhere in your /home folder, if you choose.

Another way of finding what you want is to look for "portable linux apps" or "portable linux software".

the idea behind that is that you put a few key pieces of (possibly modified) software on your thumb drive, and you can use it on any linux machine without having to actually install it.

if it can run from a thumb drive without truly being installed, it can certainly run from your home folder without truly being installed, right?

googling 'portable linux software' and 'portable apps' returns many results, none of which i know to be trustworthy/good or untrustworthy/bad... so, rather than link to any, ill leave it to you to do your own homework and come to your own conclusions :D

Unless someone here has worked with portable linux software before, and can testify to the quality of one source over another.

---

### Post by ubuntu27 on 2010-07-28
You can also encrypt just your Home directory instead of the whole hard drive.

The Ubuntu's Alternate Install CD (or Text Based Install CD) provides the option to encrypt ~/home directory upon installing Ubuntu. (Yes, you will have to reinstall. But, I've read there is a trick that will allow you to do it without reinstalling. You will have to look it up)

---

