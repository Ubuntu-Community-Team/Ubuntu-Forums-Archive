---
title: "&quot;enter password for default keyring to unlock&quot; this appears when open email applicati"
date: 2009-01-30
forum: Security
---

### Post by abc123lse on 2009-01-30
"enter password for default keyring to unlock" this appears when open email application ? what to insert ? this when I tried connect wireless DSL ...

detailed :
"Enter password for default keyring to unlock

The application 'evolution'(usr/bin/evolution) wants access to the default keyring , but it is locked.

---

### Post by Tubes6al4v on 2009-01-30
You should have set the key ring password. If you do not remember doing so, then you probably just entered you user or root password. Give those a shot. Basically what it does is just lock away all of your passwords in a file. When you enter the keyring password, the rest are automatically used... I think. I don't use a keyring.

---

### Post by argie on 2009-01-30
Try this:
1. System » Preferences » Encryption and Keyrings
2. Look at the setting: "Location for application passwords". By default this setting will be 'login'.
3. Select the corresponding Password Keyring from the list. By default this will be the 'login' keyring.
4. Click 'Change unlock password' and make that the same as your login password.

That fixed it for me.

---

### Post by abc123lse on 2009-02-02
UNDER
System » Preferences » Encryption and Keyrings
I DO NOT SEE
Look at the setting: "Location for application passwords" ANYWHERE ?

---

### Post by abc123lse on 2009-02-02
i use ubuntu 8.10

---

### Post by cjacobsen on 2009-02-02
Instead of going to the encryption settings you descrubed above go here:

Applications --> Accessories --> Password and Encryption Keys

In the "Password and Encryption Keys" manager, go to Edit --> Preferences to access and/or change to Login mode.

---

### Post by lse123 on 2009-02-02
"to access and/or change to Login mode."
describe this in more words ?

---

### Post by lse123 on 2009-02-04
problem solved some...but now when check email with EVOLUTION 2.24.3, ask me always for email passwords and if i want to create a keyring , well how avoid both ?

---

### Post by lse123 on 2009-02-11
now when check/send email ask me for my password and if i want keyring , may this get avoided and check / end email DIRECTLY ?

---

### Post by mmck on 2009-02-12
> **lse123 said:**
> now when check/send email ask me for my password and if i want keyring , may this get avoided and check / end email DIRECTLY ?

This is annoying for me also. Here is the solution:
This will erase saved passwords, you will be able to make Evolution remember the passwords of your email accounts by marking the checkbox when the program asks, after what you have done below:

   1-Open up your Home Folder by clicking Places>Home Folder
   2-click View>Show Hidden Files
   3-Find a folder called .gnome2  
   4. In .gnome2 folder, there is another folder called keyrings.  
   5. Delete all the files you find in the keyrings folder
   6. Restart the computer

After you restart, open Evolution, you will be asked for the password for your account, enter the password*, the annoying keyring manager will appear to handle the storage of that password to lock.Leave both boxes empty and click Create. The annoying second popup will ask "Store passwords unencrypted" Click Use Unsafe Storage.  From here on all passwords you enter into your computer will not be behind a keyring password.
(*If you have several email accounts you have to apply to each)

---

