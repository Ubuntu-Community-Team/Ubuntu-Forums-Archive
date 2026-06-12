---
title: "Admin user / group vs. Patron user / group"
date: 2009-05-05
forum: Security
---

### Post by marianlibrarian on 2009-05-05
I am having a hard time understanding how authorizations and privileges work for users. I have myself set up as an admin user in the admin group. Then I have patrons set up as patron in the patron group.

I just recently read a thread that said to make sure that users are in their correct group. I originally did not have any user assigned to any group.

I need to limit the patron group so that this user cannot move the panels or have access to the majority of menu items found under the System menu. It would be nice if I could remove the Administration menu item from the Patron user's menu, but still have it available when the Admin logs in.

I found something called ubuntu-tweak and installed it. It is nice but it is added to the Applications / System Tools menu. I tried to block this from user Patron by going through Authorizations from the Administration menu. But this item is still available to the Patron user. It doesn't even ask for their password. 

I have also explored Pessulus and liked it. But again this item is available from the Administration menu.

I know many have suggested Kiosk setup. I am desperate right now. My summer reading program is getting into full swing and I am by myself in this endeavor. I won't be able to learn and apply myself to a Kiosk setup until July or August.

Could someone please explain how to properly set up a user and how to limit access to menu items such as hiding the Administration Menu from the low level user.

---

### Post by marianlibrarian on 2009-05-05
I have searched through the forums with many different search terms and have not found any information that answers this. I came to this section "Security Discussions" first. Perhaps I should have posted this in the Absolute Bunny Slope section?

May I move this thread there or is that the dreaded cross posting offense?

---

### Post by marianlibrarian on 2009-05-05
Rather than letting this languish here (I didn't mean to post in the wrong section) and move this to the Beginners section. Thanks.

---

### Post by bodhi.zazen on 2009-05-05
The process of setting up a kisok is laid out , step-by-step, on the link you have been given (on another thread).

Install Kubuntu or Ubuntu and follow the steps :

KDE :

[http://developer.kde.org/documentation/tutorials/kiosk/index.html](http://developer.kde.org/documentation/tutorials/kiosk/index.html)

Gnome :
        [http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)


If you are having problems, rather then starting multiple threads and asking for step-by-step guides, please tell us what specific question you have. Please be sure to tell what guide you are suing an which step is problematic.

To answer your question about groups :

[uwiki]FilePermissions[/uwiki]

The last piece of advice I can give you is to step back and consider if this is feasible for you right now. From your posting style it sounds as if you are taking on more then you can manage right now. Ubuntu is not a drop in replacement for Windows and it will take you time to learn a new OS. By that I mean you had to re-install to fix a problem with the way panels were set up (in a previous post) ? Fixing panels is a very basic task and while re-installing is a solution, it is obviously unrealistic.

I am not trying to be rude, just bring you back to reality.

Personally, if you are going to be responsible for managing these machines personally, you need to first learn how to run Linux. Then roll out the project for others.

---

