---
title: "Login Issue 11.10"
date: 2011-12-06
forum: Ubuntu Studio
---

### Post by PRnate469 on 2011-12-06
Excuse me if this is already posted, but I didn't find one. **Background:**  I am having an issue with logging in to Ubuntu Studio 11.10. I have a laptop x64, and has 2 partions. One has Windows 7, and the other has Ubuntu Studio 11.10. Ubuntu was installed with encrypted /home, and everything in one partion (except for /swap of course). This was a fresh install, and everything was working great actually. I created another account (not sure if encrypted or not), and then saved the password so it doesn't have to be typed when you try to login. This isn't a huge issue, but I would like to note that I could never login to that new account. It kept giving me a black screen and then back to the login page. I could still login to the main account, and I could also use guest. After about a day of the new account being created, I shut my computer down. The next morning I loaded Ubuntu up, and started to login. **The Issue:** When trying to login to the main user I get a blank screen, and sends me back to the login screen. I can login to gues, and I can even use ctrl alt f1 and login to the main account like that. **Stuff I tried so far:** *ls - shla | grep "xauthority"/ sudo mv ~/.Xauthority Xauthority.old/* then restart (sudo shutdown -r now). nothing. I deleted the alt account (sudo userdel username), and that didn't do anything either (shot in the dark I know but i'm grasping for strawls here and keep pulling the short one. lol) It's been awhile since i've actually had to do anything real technical on linux other than samba configuring. Can anyone help with this issue? OH! I also read somewhere about amount of disk space taken up. *df -h* shows 99g free.

---

