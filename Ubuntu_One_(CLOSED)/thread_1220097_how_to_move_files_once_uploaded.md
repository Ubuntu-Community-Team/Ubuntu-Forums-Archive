---
title: "how to move files once uploaded"
date: 2009-07-22
forum: Ubuntu One (CLOSED)
---

### Post by GoldenSun on 2009-07-22
I uploaded some files, but decided to make a folder.  Now I want those uploaded files in the new folder.  How do I do that without having to re-upload everything to the new folder.

---

### Post by Cyked on 2009-07-22
What specifically are you doing when you say you uploaded files?

How are you uploading?  If you have ssh access you can do a cp command to move the files from one location to another...  Or maybe even via the tool you are using to upload (ftp, sftp?)

Something like....
```
cp /home/user/files home/user/upload
```

---

### Post by GoldenSun on 2009-07-22
This is my second day on it, but I'm using my work windows machine right now.  I was just on the website and would press the upload button.  

I didn't know there was ssh access.  how do you access it.  (host name?)
I already have putty n' filezilla; and I got the commands down.

---

### Post by Cyked on 2009-07-22
> **GoldenSun said:**
> This is my second day on it, but I'm using my work windows machine right now.  I was just on the website and would press the upload button.  

I didn't know there was ssh access.  how do you access it.  (host name?)
I already have putty n' filezilla; and I got the commands down.

Sorry, still confused.  What are you uploading to?

---

### Post by raronson on 2009-07-22
Totally off-topic:

Two thumbs up for Cyked's "Arrogant B@stard Beer" avatar.  Good stuff.

---

### Post by GoldenSun on 2009-07-22
> **Cyked said:**
> Sorry, still confused.  What are you uploading to?

uhh ok I am accessing it through a browser.  like I am on the ubuntuone website.  I log in and click the "upload" button.  I select a file and it uploads.  

I don't know how much better I can explain it lol.

Anyways I think I might know what I need to do.  
I'm guessing make a new folder in the ubuntuone folder in the home directory.  let's call it "music".  so it's in...
/home/user/ubuntuone/My\ Files/music

Then I'll just filezilla the files I need to the music directory and delete the files I already uploaded on the website.

---

### Post by Cyked on 2009-07-22
LOL.  Got it, sorry.  I totally missed the forum tag and assumed you were talking about sftp or something.

Remember kids, reading is fun-da-men-tal. ](*,)

---

### Post by cbtengr on 2009-07-22
> **GoldenSun said:**
> I uploaded some files, but decided to make a folder.  Now I want those uploaded files in the new folder.  How do I do that without having to re-upload everything to the new folder.
I was able to create a new sub folder in the browser interface, but could only move the existing files into it using the local Ubuntu One client.  I don't know if the files were uploaded again or if they were just moved via the Ubuntu One folder action.

---

### Post by enz1m3 on 2009-07-22
I believe there is a command to move, but appropriately, now that I was going to check and tell you, the login is down... this happens when I click login "OpenID discovery error: HTTP Response status from identity URL host is not 200. Got status 404"

---

### Post by cariboo on 2009-07-22
Launchpad was down for scheduled maintenance earlier today.

---

### Post by GoldenSun on 2009-07-23
Basically you have to manage all your files in the ubuntu one folder and not the browser interface.  The only thing to use the browser interface for is to download files are to share with someone.  

Also my problem is still present.   I have a folder created through the browser interface and it won't go away after I click delete.

---

### Post by enz1m3 on 2009-07-24
Where did you delete? the Ubuntu One folder (I didn't find that working well) or the Ubuntu One webapp (This works fine for me)?

---

