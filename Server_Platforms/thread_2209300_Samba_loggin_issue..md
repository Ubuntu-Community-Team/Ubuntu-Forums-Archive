---
title: "Samba loggin issue."
date: 2014-03-05
forum: Server Platforms
---

### Post by 4hzAzpw on 2014-03-05
Hey there,

I'm having an issue with my samba share on my 12.04 Ubuntu Server. 

The share folder works fine and i'm able to read and write only when i'm logged into the server. 
If I boot the server the share folder is visible but i'm unable to access it.
Once I log into the server the share works perfectly.

Anybody got any ideas?

---

### Post by SeijiSensei on 2014-03-05
That's the correct behavior unless you set up a "public" share in smb.conf.

---

### Post by thufirhawat2 on 2014-03-05
I had this issue in testing when I initially set my server up. Is the share located in a user home directory? When you set that user up, did you encrypt the home directory? 

From my experience, if you encrypt the home directory, and your share is located there, you have to SSH to, or locally login to the server manually to be able to access the samba share. I did not do a lot of follow up research on it, I just reloaded and did not encrypt the home directory, and from there on had no issues with being able to access the share whether the user is logged in or not. For sensitive data, I just use truecrypt and made a file container to put important things in, but I am not wholly concerned about my hiking pictures, music, and movies being encrypted. Hope this helps.

---

### Post by 4hzAzpw on 2014-03-05
Thanks for your replies guys.

I'll change the location of the share folder and see if that helps thufirhawat2.

---

### Post by eborghi1 on 2014-03-06
> **SeijiSensei said:**
> That's the correct behavior unless you set up a "public" share in smb.conf.

I had the same issues with 12.04 LTS while in 13.10 the exact setup didn't lock me out and did honor my "users =" and revalidate parameters perfecty without requiring me to log into the server. In 12.04 I did have to log into the server and that was successful but when I tried to access the share after logging into the server the share could not be accessed due to "permissions". With 777 that shouldn't be a problem. Yes I know 777 is not a good idea and I only did it for testing after I started to have problems. 

So am asked to log into the server. That is successful.
Then I am asked to supply a user name and password for the share. That is when I get the permissions error.

---

### Post by 4hzAzpw on 2014-03-06
Thurfirhawat2 was right.

I moved the share folder to a different location and out of my home directory and the share works normally now. 

Thanks for your help.

---

