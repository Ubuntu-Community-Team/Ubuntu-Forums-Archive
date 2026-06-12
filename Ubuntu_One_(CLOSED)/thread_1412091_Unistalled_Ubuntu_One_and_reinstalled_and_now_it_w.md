---
title: "Unistalled Ubuntu One and reinstalled and now it wont work."
date: 2010-02-20
forum: Ubuntu One (CLOSED)
---

### Post by markinf on 2010-02-20
So after much hate of Ubuntu One I uninstalled, --purged, and got rid of it. No I'm thinking of giving a second chance. I reinstalled, but IT JUST WON'T SYNC. It's just says your files are up to date...

---

### Post by andrea000 on 2010-02-21
I think you will need to add your computer to the u1
website again something happens when you remove it.

---

### Post by joshuahoover on 2010-02-22
> **markinf said:**
> So after much hate of Ubuntu One I uninstalled, --purged, and got rid of it. No I'm thinking of giving a second chance. I reinstalled, but IT JUST WON'T SYNC. It's just says your files are up to date...

I'm sorry to hear Ubuntu One hasn't been working properly for you. Did you get a prompt in your web browser to add your computer? When you open Ubuntu One for the first time you should get prompted to add your computer to your Ubuntu One account within a browser window. If you don't ever see this page, can you try the following?

1) Quit the Ubuntu One client (right-click on the Ubuntu One client applet and select "Quit")
2) From a terminal session (Applications->Accessories->Terminal): ubuntuone-client-applet

Is there any information output? If not, can you try this command from a terminal session?

apt-cache policy ubuntuone-client

If you're not using NetworkManager, then you'll need the latest version of Ubuntu One installed. You can do this by running System->Administration->Update Manager. 

If you continue to have problems you can either file a bug by right-clicking on the Ubuntu One client applet and selecting "Report a problem" to file a bug or you can hop on #ubuntuone on Freenode IRC and ask for joshuahoover. I'm available 14:00 to 22:00, Monday thru Friday. If I'm not there, you can ask for rye and he's normally available earlier than I am during the weekdays.

Thank you,

Joshua

---

