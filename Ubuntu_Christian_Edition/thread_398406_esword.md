---
title: "esword"
date: 2007-04-01
forum: Ubuntu Christian Edition
---

### Post by kiwidipstick on 2007-04-01
Hi again, may I request help from Mhancoc7 please.
I have already posted about my problem of not being able to install The Message Bible using esword  module manager.
Would you be able to offer suggestions as to how to install this module.

I look forward to your reply Jereme, trusting in the Lord at all times, James.

---

### Post by mhancoc7 on 2007-04-01
> **kiwidipstick said:**
> Hi again, may I request help from Mhancoc7 please.
I have already posted about my problem of not being able to install The Message Bible using esword  module manager.
Would you be able to offer suggestions as to how to install this module.

I look forward to your reply Jereme, trusting in the Lord at all times, James.

Hi James,
I am not sure why you are having trouble with the installation of The Message. There have been others that have had no issue with installing any of the pay modules. 

First let me ask, are you using a language other than English in Ubuntu CE? Also, could you describe the exact issue that you are having with the installation of the module? Also have you tried to download any of the other free modules and then install them manually?

Thanks, Jereme

---

### Post by kiwidipstick on 2007-04-01
Hi Jereme,

Firstly,  yes I have installed about four of the free Bible modules with no problems.I am using the English language,

I downloaded the Message Bible after paying for it, then I started up e-sword module manager, went to the manual tab and pointed to my download folder, and then clicked Install Module.

The response is; Starting, Getting Module, Installing Module, then a separate window saying Preparing wizard, please wait...

And that is it. Yesterday, I left it alone for 3 hours when we went to Church, but upon our return it had not budged. This was my third attempt to get it to install.

By the way, I have disabled Dansguardian. 

Puzzling isn't it. I look forward to your reply Jereme,
Blessings, James.

---

### Post by kiwidipstick on 2007-04-01
oops, sorry Jereme. The free modules were installed automatically, not manually. James.

---

### Post by mhancoc7 on 2007-04-01
> **kiwidipstick said:**
> oops, sorry Jereme. The free modules were installed automatically, not manually. James.

Ok, I am really not sure what is going on. Could you please download one of the free download modules and try to install it manually and let me know what happens. The other thing that you could do is to install The Message into e-Sword on a Windows machine and then manually copy the module files into the e-Sword directory in Ubuntu CE. 

God Bless, Jereme

---

### Post by kiwidipstick on 2007-04-01
Quote: [I]Ok, I am really not sure what is going on. Could you please download one of the free download modules and try to install it manually and let me know what happens. The other thing that you could do is to install The Message into e-Sword on a Windows machine and then manually copy the module files into the e-Sword directory in Ubuntu CE.
[/I]
Well, I tried your suggestion and it worked fine for the manual d/l and install. Still wont work for the paid module. Is it possibly something to do with the email address and key window?

I'd rather not have to go the windows route if possible, but if I do have to, where are the modules stored in Ubuntu?

Blessings to thee again, James.

---

### Post by mhancoc7 on 2007-04-02
> **kiwidipstick said:**
> Quote: [I]Ok, I am really not sure what is going on. Could you please download one of the free download modules and try to install it manually and let me know what happens. The other thing that you could do is to install The Message into e-Sword on a Windows machine and then manually copy the module files into the e-Sword directory in Ubuntu CE.
[/I]
Well, I tried your suggestion and it worked fine for the manual d/l and install. Still wont work for the paid module. Is it possibly something to do with the email address and key window?

I'd rather not have to go the windows route if possible, but if I do have to, where are the modules stored in Ubuntu?

Blessings to thee again, James.

I really have no idea why it is not working. :(

The Bible modules are stored in the following directory:
"/usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword"


God Bless, Jereme

---

### Post by kc1di on 2007-04-02
> **kiwidipstick said:**
> Quote: [I]Ok, I am really not sure what is going on. Could you please download one of the free download modules and try to install it manually and let me know what happens. The other thing that you could do is to install The Message into e-Sword on a Windows machine and then manually copy the module files into the e-Sword directory in Ubuntu CE.
[/I]
Well, I tried your suggestion and it worked fine for the manual d/l and install. Still wont work for the paid module. Is it possibly something to do with the email address and key window?

I'd rather not have to go the windows route if possible, but if I do have to, where are the modules stored in Ubuntu?

Blessings to thee again, James.

I know you've been Asking Jereme and He is the person to ask technical Question,  But in reading the posts I did not see a mention of the lock key enter window.. It was hidden under the install window when I purchase the word study program .. you have to eneter the key they should have sent you by email If you did not get it you need to email and explain you did not get it.  Also if I remember right the key is case sensitive. 
hope this helps 
blessings David

---

### Post by kiwidipstick on 2007-04-02
Quote:
[I]Originally Posted by kiwidipstick View Post
Quote: Ok, I am really not sure what is going on. Could you please download one of the free download modules and try to install it manually and let me know what happens. The other thing that you could do is to install The Message into e-Sword on a Windows machine and then manually copy the module files into the e-Sword directory in Ubuntu CE.

Well, I tried your suggestion and it worked fine for the manual d/l and install. Still wont work for the paid module. Is it possibly something to do with the email address and key window?

I'd rather not have to go the windows route if possible, but if I do have to, where are the modules stored in Ubuntu?

Blessings to thee again, James.
I know you've been Asking Jereme and He is the person to ask technical Question, But in reading the posts I did not see a mention of the lock key enter window.. It was hidden under the install window when I purchase the word study program .. you have to eneter the key they should have sent you by email If you did not get it you need to email and explain you did not get it. Also if I remember right the key is case sensitive.
hope this helps
blessings David[/I]

Hi David, thanks for your input. Yes, I did enter the details for my email address and for the key. 
The 'key' window accepted the code okay, as the first time I entered it, I got it wrong and I was informed that the key was wrong.
It's beyond me. Perhaps, as Jereme suggested, I will have to install in Windows and copy that module out into Ubuntu CE.

Blessings, James.

---

### Post by tak1150 on 2007-04-05
I was struggling with installing NKJV module (you have to pay for it) as well and tried simply copying the nkjv.bbl from the Windows OS (/Program Files/e-Sword/nkjv.bbl) and pasting it into /usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword.
And it WORKED! Praise the Lord!

---

### Post by kiwidipstick on 2007-04-05
> **tak1150 said:**
> I was struggling with installing NKJV module (you have to pay for it) as well and tried simply copying the nkjv.bbl from the Windows OS (/Program Files/e-Sword/nkjv.bbl) and pasting it into /usr/local/apps/esword4linux/.esword/drive_c/Program Files/e-Sword.
And it WORKED! Praise the Lord!

Hi tak1150, I did what you suggested worked for you, but, when I reached c_program files/e-sword, there is another 2 folders; 1, program files, 2, windows. Inside the program files is another 2 folders, common or e-sword. I pasted into the e-sword folder, to no avail.
Oh boy, any ideas?

Blessings, James.

---

### Post by Slothbert on 2007-09-06
Thanks for your help! It worked like a charm!:)

---

