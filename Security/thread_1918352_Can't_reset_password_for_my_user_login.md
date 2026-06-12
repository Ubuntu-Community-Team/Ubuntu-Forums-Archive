---
title: "Can't reset password for my user login"
date: 2012-01-31
forum: Security
---

### Post by Nekrosilisk on 2012-01-31
I'm using Ubuntu 11.10.  I haven't lgged in for about a month and as a result have forgotten my password.  Fortunately my account is set to login automatically so i can still access my programs, but i can't install any updates.  I'm new to Ubuntu, and am still learning how the system works.

Using online searches i was able to find the basic method to reset it using GRUB.  However whenever i attempt to reset with passwd username, I receive an authentication error.  how do i get around this?

---

### Post by uRock on 2012-01-31
This may be helpful. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Nekrosilisk on 2012-02-01
Thanks for the link URock.  I used ls /home to verify i was inputing my username correctly.  However when i attempt to alter my password I'm still receiving a notification that says "Authentication token manipulation error."

---

### Post by uRock on 2012-02-01
Is your /home encrypted? If yes, this will change the game drastically.

---

### Post by Nekrosilisk on 2012-02-01
I don't know.  I had the CST guys here at Job Corps install Ubuntu after Windows crashed last time.  How would I check to see if it is.  I still have access since my profile automatically signs on.

---

### Post by cariboo on 2012-02-01
The easiest way to check if your home directory is encrypted is to start in recovery mode, and once at the menu select the mount drives option, then select drop to a root prompt. Once at the prompt cd into your home directory eg:

```
cd /home/username
```

where username = your user name, then try to read one of the files in the directory.

---

### Post by Nekrosilisk on 2012-02-01
What is the command to view a file?

---

