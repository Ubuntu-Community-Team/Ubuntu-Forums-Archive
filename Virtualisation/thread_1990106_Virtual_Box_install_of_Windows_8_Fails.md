---
title: "Virtual Box install of Windows 8 Fails"
date: 2012-05-29
forum: Virtualisation
---

### Post by Curtis6767 on 2012-05-29
I installed VB and then Lubuntu, and that install went well. I even installed Mageia 2 with good luck. But I cannot install Windows 8. 

I have set up VB to install from the iso in my downloads folder and also from a DVD and I get to about the same place in the install and then the install stops.

I've scoured the web looking for tips on how to do this but so far nothing I've found has allowed for success.

I get to the first screen and get to about the 80% point and then the install stops.

Then I get this error message thats on the second image.

The rest of the images, and those in part II of this post  show how I've got this install set up. I've fiddled with these settings many times but so far I cannot figure the right combination. There is also the possibility that my image is corrupt, but I just don't think that's the case. I haven't been able to find the checksum for Windows 8, but I'm headed out to do just that after I finish this post.

---

### Post by Curtis6767 on 2012-05-29
Here are the rest of the images which showing system settings.

If you have had success installing Win8 Consumer Preview via VB, I'd really like to know how you did it, or, if you know what I'm doing wrong, please let me know.

Thanks

---

### Post by Cheesemill on 2012-05-29
I've just installed this myself yesterday and had no problems using the default VM settings (which are the same as yours). It sounds like a bad .iso image to me.

You can find the SHA checksums for the .iso file here:
[http://windows.microsoft.com/en-GB/windows-8/download](http://windows.microsoft.com/en-GB/windows-8/download)

---

### Post by Curtis6767 on 2012-05-29
> **Cheesemill said:**
> I've just installed this myself yesterday and had no problems using the default VM settings (which are the same as yours). It sounds like a bad .iso image to me.

You can find the SHA checksums for the .iso file here:
[http://windows.microsoft.com/en-GB/windows-8/download](http://windows.microsoft.com/en-GB/windows-8/download)

I suspected the same about the iso but I've been too busy to check the checksum, so thanks for that link.

I noticed a lock over the iso in my downloads folder and I assumed it was locked by MS and that having the key would take care of that. I've just downloaded a new image and it doesn't have that lock. I'm about to install it so we'll see if that's what it was.

Thanks

---

### Post by Curtis6767 on 2012-05-29
Success!

I found the checksum here: [http://windows8forums.com/windows-8-discussion/5253-windows-8-consumer-preview-frequently-asked-questions-faq.html](http://windows8forums.com/windows-8-discussion/5253-windows-8-consumer-preview-frequently-asked-questions-faq.html)

Apparently it was a bad ISO image because the second download produced a successful install.

Two things I did wrong:

When I first clicked on the Download button over at MS, Brasero popped up giving me the option to open with it or to save. I wasn't paying attention and I just clicked on open. At the end of the download, Brasero popped up again and it wanted to burn the ISO. I've had problems with Brasero in the past and now use K3b, so I canceled out of Brasero.  This could be what corrupted the ISO. Just guessing.

Second was in the window that pops up that asks for the type of machine and then guest OS, I selected Linux. LOL. Eventually I figured this one out and selected Windows.

So that's it. Win8 seems to be running well, though I've only loaded it once. Hopefully the next time I load it it will just start up and go.

---

