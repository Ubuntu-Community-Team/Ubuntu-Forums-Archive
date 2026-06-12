---
title: "WPUT woes"
date: 2012-03-05
forum: The Cafe
---

### Post by steveodeevo on 2012-03-05
I have been trying to ftp up a webcam image from a folder using WPUT, which I have previously used to upload webcam images from my netbook running via cron.

My web host software (kloxo) creates user accounts with an ftp account as standard, however I added a new one for the webcam, it doesn't have many options really, and certainly nothing like encryption.

However uploading on primary ftp account works fine, but gets interupted when in use, uploading on the new one, comes back with the following error,

My command:
> 
/usr/bin/wput /home/[user]/webcam/webcam2.jpg [ftp://[username]:](ftp://[username]:)[pass]@[host]/webcam2.jpg


The result:
> 
Connecting to [host]:21... connected! encrypted!
Logging in as webcam2 ... Error: Login-Sequence failed (Authentication failed, sorry)


Now I have googled this, and find no option to enable or disable encryption in WPUT, and as I said my server has no features to encrypt ftp accounts, so I am a bit confused by this.

So I thought I would post up here to ask if anyone has a clue as to what is going on, as 2 ftp accounts on same server, which are not encrypted, and one connects fine with exactly the same WPUT command line, and the other fails complaining of encryption errors!  Strikes me that both should work fine, and I rebooted the server just to make sure it was nothing silly, but to no avail.

---

