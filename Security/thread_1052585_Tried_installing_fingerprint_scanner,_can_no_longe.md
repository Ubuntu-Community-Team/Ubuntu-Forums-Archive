---
title: "Tried installing fingerprint scanner, can no longer login."
date: 2009-01-27
forum: Security
---

### Post by iamyourdemize on 2009-01-27
So I am working on an HP Laptop with a fingerprint scanner. I tried setting it up today and was playing around with pam.d/common-auth. Now when I try logging into Ubuntu it says Authentication failed. 

HELP! Oh, and I have very little idea what I am doing in Ubuntu as I am a newbie so if you have an idea can you explain it VERY detailed. Thanks guys!

---

### Post by pedja_portugalac on 2009-01-27
> **iamyourdemize said:**
> So I am working on an HP Laptop with a fingerprint scanner. I tried setting it up today and was playing around with pam.d/common-auth. Now when I try logging into Ubuntu it says Authentication failed. 

HELP! Oh, and I have very little idea what I am doing in Ubuntu as I am a newbie so if you have an idea can you explain it VERY detailed. Thanks guys!

I never tried to make finger print check work on ubuntu cause I had problems loging in even when originally my computer came with vista. 7 times out of 10 it wasn't able to read right my finger print. Forger finger print and think about strong password.

---

### Post by iamyourdemize on 2009-01-28
> **pedja_portugalac said:**
> I never tried to make finger print check work on ubuntu cause I had problems loging in even when originally my computer came with vista. 7 times out of 10 it wasn't able to read right my finger print. Forger finger print and think about strong password.

Yeah, I ended up removing the what I installed but forgot to remove a line from the pam.d file. Can anyone help me?

---

### Post by Nepherte on 2009-01-28
Boot in recovery mode or with a live cd and fix the file.

---

### Post by teddks on 2009-01-28
I don't think recovery mode will work, because it will still go through PAM for the login. A boot CD is your only option.

---

### Post by bmwman on 2009-01-29
I had the same problem and you can go to recovery mode and uninstall the fingerprint software. I'm not sure what did you install but I think I used thinkfinger or something like that. You shouldn't enable it until you make sure your fingerprint is saved successfully and most of the times you need to try like 30 time untill it takes it. At least that's what  I did.

---

### Post by hyper_ch on 2009-01-29
I wonder why you use a fingerprint reader at all...

---

### Post by Kirizan on 2009-02-04
> **hyper_ch said:**
> I wonder why you use a fingerprint reader at all...

I used to wonder that myself till I had one. It's not a security thing, it's a convenience thing. It's nice to be able just swipe your finger and log into a page. 

Yes, it makes me lazy, and yet, I just can't seem to care :)

---

### Post by sholay-ramana on 2009-07-01
I have installed fingerprint reader in pc running on ubuntu.i could enroll users and verify in Terminal.I want to do the same in browser.i have a form in php page with username and password.when user enters username,password and swipe a finger, it should store all the data in database.so, from next time onwards, user will enter username,password and swipe finger to login.we will have to authenticate checking with the values of database.can any body help me?

---

### Post by sparticus4 on 2009-07-07
I have an Asus laptop with a fingerprint reader and a camera the camera works but im upside down but the finger reader doesnt work i need help in getting these to both work.


Thank you

---

### Post by samiux on 2009-07-08
> **iamyourdemize said:**
> So I am working on an HP Laptop with a fingerprint scanner. I tried setting it up today and was playing around with pam.d/common-auth. Now when I try logging into Ubuntu it says Authentication failed. 

HELP! Oh, and I have very little idea what I am doing in Ubuntu as I am a newbie so if you have an idea can you explain it VERY detailed. Thanks guys!

I successfully make fingerprint on my Lenovo ThinkPad X61 work.

[http://samiux.wordpress.com/2008/11/22/howto-ubuntu-810-on-lenovo-thinkpad-x61/]("http://samiux.wordpress.com/2008/11/22/howto-ubuntu-810-on-lenovo-thinkpad-x61/")

---

