---
title: "How-to install Zimbra Desktop"
date: 2011-04-03
forum: Tutorials
---

### Post by Alfons81 on 2011-04-03
Hi all, here we go:

1. Download Linux package from: 

[www.zimbra.com/products/desktop.html]("http://www.zimbra.com/products/desktop.html")

2. Extract the content of the package (*.tar.gz) on your Home, Desktop...right click > Extract here

3. Open a terminal and go where you extract zimbra...for example:

$ cd home/<user_name>/Desktop/zdesktop_2_0_1_b10659_linux_i686/

4. from that path run:

$ sudo ./install.pl

5. It will guide you to the Setup Zimbra Desktop > press (A) to accept terms and conditions 

6. If you would, accept the default directori where it install 

/opt/zimbra/zdesktop

7. Would you like to continue to install files for user: Root? > Here you may want to answer NO...otherwise you always have to log in Zimbra Desktop as superuser.

8. To install data files run this command (always on the same path: ~//Desktop/zdesktop_2_0_1_b10659_linux_i686/):

$ /opt/zimbra/zdesktop//linux/user-install.pl

9. Now you'll be asked about where to install files, for example:

Home/<user_name>/.zdesktop

(if you put a dot in front zdesktop, it'll be hidden (ctrl+h) inside your home folder...)

10. And then you'll be asked about the path where to locate the icon where you'll launch Zimbra, for example:

/home/<user_name>/Desktop

11. Press enter and configure your accounts. It is a really usefull, and complete aplication. You have tabs to manage facebook,twitter accounts, calendar, tags...

Enjoy, Cheers

---

### Post by fooey on 2011-04-04
thx

---

### Post by tonyman68 on 2011-09-01
I was unable to run the following command To install data files run this command (always on the same path: ~//Desktop/zdesktop_2_0_1_b10659_linux_i686/):

$ /opt/zimbra/zdesktop//linux/user-install.pl. I got an error errors.

Generally, I have not been able to run any commands. I was getting error messages. What I did was to find executable files and I eventually installed the email client. I downloaded the latest version from zibra website.

Whenever I click the zimbra zdesktop icon on the desktop, it does not start.

Any kind of help is welcome
Many thanks in advance
Cheers
Tony

---

### Post by Alfons81 on 2011-09-12
Hi 

You have to look at the version of Zimbra, since I wrote this tutorial it might grow. Then you need to change it on that command (not just copy paste this command). 

What kind of error message are you getting?

What you mean saying that generally you cannot run commands?

---

### Post by isalovell on 2012-05-14
I have been trying to install Zimbra desktop in my ubuntu 11.04, but every time I do so, it installs as root user. Any help in turning this to install as normal user???

---

### Post by Snib on 2012-05-22
@Isalovell,

In the post from Alfons81, on this thread, see step 7 - you must say No at this point to ensure it is not installed under the root userid. 

Then step 8, run the command:

/opt/zimbra/zdesktop//linux/user-install.pl

ensure you do not prefix this with "sudo" so the command is executed under your user id, not root. Basically answer Yes to the prompts as this command runs and this should install Zimbra under your userid. 

Hope this helps.

---

