---
title: "Got empty result for devices list"
date: 2010-05-11
forum: Ubuntu One (CLOSED)
---

### Post by ghosTM55 on 2010-05-11
Hi all , I get ubuntu 10.04 LTS installed on my PC and laptop , and I tried ubuntu one.
It worked and I want to have a test, so I removed the two devices that already subscribed to my ubuntu one account, after that, I found I can't get them subscribed back.
Everytime I start ubuntu one preference , I'll get the error message: got empty result for devices list.
How can I add my two devices back to my ubuntu one account , any help? Thanks!

(I googled a lot and found that someone pointed that delete the ubuntu one's key will work, so if this is the right solution, how to delete it? Thanks again)

---

### Post by duanedesign on 2010-05-11
If after deleting a Device from your list and you then have problems adding that device you will want to do the following to ensure it was completely removed.

   1. Quit the Ubuntu One Preferences window
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Me Menu -> Ubuntu One or System -> Preferences -> Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer

Some users have reported problems with finding the "**Add Your Computer"** button in this process. If that is the case try the following.

   1. close the Ubuntu One Preferences application window (if it's already open)
   2. open your Terminal (located in Applications -> Accessories)
   3. and type the following: 

```
 u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

This should force a web browser to open and put you at step 2 of [this process]("https://one.ubuntu.com/support/installation/")

---

### Post by Rong42 on 2010-05-11
it sounds like you have a similar problem to me, this sorted me out:

[https://answers.launchpad.net/ubuntuone-client/+question/110224](https://answers.launchpad.net/ubuntuone-client/+question/110224)

---

### Post by Lylex11 on 2010-05-24
Thanks, this worked for me. But now I see that Tomboy Notes are missing the option to sync with the ubuntuone server, only filesystem.

---

### Post by ninjitisu on 2010-06-11
Thanks, this worked for me too :p

---

### Post by divxclub on 2010-06-16
Thanks a lot guys this problem was driving me crazy and I didn't know what is goin on. we got solution however is this something that some sort of a bug or justuser error because it looks like that if you reistall ubuntu on same system this will happen again and again.  Thanks a lot !

---

