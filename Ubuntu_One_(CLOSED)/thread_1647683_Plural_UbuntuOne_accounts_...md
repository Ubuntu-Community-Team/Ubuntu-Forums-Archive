---
title: "Plural UbuntuOne accounts .."
date: 2010-12-17
forum: Ubuntu One (CLOSED)
---

### Post by balise on 2010-12-17
I have been slow to put my Meerkat Ubuntu onto UbuntuOne, but after a week-long successful recovery of sda partition table, I want to.

However I have somehow signed up three times, and it doesn't seem to log me into any of my incarnations (jae@c-art.com is latest, but I have another [email]jae@c-art.com[/email] with a different password, as well as [email]both.and.each@gmail.com[/email]).

I don't see how to mail to an administrator at UbuntuOne.

-jae

---

### Post by duanedesign on 2010-12-18
To see which account your computer is currently using you can do the following:

1. Open System > Preferences > Password and Encryption Keys

2. Find the Ubuntu One Token, right-click and select Properties.

3. Click the triangle next to Password and then check Show Password.

4. Look for and note the part after 'token='

5. Open [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)

6. Compare the number and letter sequence you noted in step 4 to the sequence in parenthesis, after your computer name, in step 5.


If you need to clear your computer and add it to a different account try the following steps.

1. Quit the Ubuntu One Preferences, if open
2. Open (Lucid): Applications->Accessories->Passwords and Encryption Keys (Maverick): System -> Preferences -> Password and Encryption Keys
3. Click on the arrow next to "Passwords"
4. Right-click on the Ubuntu One token and select "Delete"
5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
6. Click on the checkbox next to your computer
7. Click the "Remove selected computers" button
8. (Maverick): killall ubuntu-sso-login; u1sdtool -q; u1sdtool -c
(Lucid): u1sdtool -q; killall ubuntuone-login; u1sdtool -c
9. a web page, if in Lucid, or a window, in Maverick, should open,prompting you to add your computer to your Ubuntu One account
10. Add your computer

---

