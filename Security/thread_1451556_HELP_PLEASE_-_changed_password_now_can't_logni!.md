---
title: "HELP PLEASE - changed password now can't logni!"
date: 2010-04-10
forum: Security
---

### Post by Ceiber Boy on 2010-04-10
I'm running 64-bit Ubuntu Karmic, Encrypted HDD.

I changed my login password

when i try to boot i click on my name and type in my new password i have 'authentication fail' when i type in my old password this happens

"could not update ICEauthority file /home/chris/ICEauthority"

"Their is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2) exited with status 256"

"Nautilus could not create the following required folders
/Home/chris/Desktop,/home/chris/.nautilus
Before running nautilus, please create these folders, or set permissions such that nautilus can create them."

anyone any ideas please!!!

---

### Post by Ceiber Boy on 2010-04-10
ok

what i think happened was when i changed my password it changes the HDD encryption password, and not the unix password, thus causing me to have two passwords, one for the login screen and another to decrypt the HDD. So when i went to login my HDD password did not allow me to login and my original login password no longer decrypted the HDD.

So logging in as root under the recovery option i used the terminal to change my unix password from my old password to the same password i use to decrypt the HDD. So, now that both the passwords are the same i can login without any problems.

I hope all that made sense!

If anyone can provide a more technical explanation i would be pleased to read it.

---

### Post by Jive Turkey on 2010-04-10
I think you have it reversed.  sudo passwd username probably changed your unix password but did not change the setup for decryption.  Interesting problem, and you should probably file a bug for the package ecryptfs.

---

### Post by darkshadow on 2010-04-10
You should make a bug report because I had the same problem before. I could change my password with the Gnome GUI and it would automatically change the encryption one also.
But then once I used the passwd command from a terminal and it caused the same errors you had. I fixed them by using ctrl+alt+F1 then logging in and using the passwd command again to go back to my old password.

---

### Post by nbros652 on 2010-04-12
I had the same problem, and couldn't change back to the old password because passwd said my old password was not secure enough and refused to use it. I did however find a solution to my problem which I have detailed below. The source of my problem, I discovered, was that my home directory was encrypted, and when I changed my login password, the home directory password was not changed at the same time. Here's how I fixed it...

1. Upon a restarting the computer I got an error that said something like "Could not update ICEauthority file /home/user/.ICEauthority" ...
2. When these errors come up, push [ctrl] + [alt] + [F1] (don't know if it makes a difference or not but I used left control and left alt)
3. At the terminal that comes up, enter your user login name
4. When it asks for a password, use your new login password that you recently changed to
5. You should now be logged in. Enter the following command in the terminal and when asked for your password, enter your old login password
  ```
ecryptfs-mount-private
```6. Your encrypted home directory should now be mounted, but you still need to refresh it. Enter the following command:
  ```
cd ~
```7. Now you have full access to your encrypted home directory and can browse it as normal. The only thing left to do is to change the password on your home directory to match your login password. Enter the command below. When asked for your old password, use the same password you used in step 5. When asked for the new password, be sure not to make any mistakes as you will not be asked to confirm the password. Make your new password the same as your new login password.
  ```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```8. Now restart your computer using the command below. If you did everything correctly, everything should load up just like it used to.
  ```
sudo shutdown -r 0
```

---

