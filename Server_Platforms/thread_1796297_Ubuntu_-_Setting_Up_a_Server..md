---
title: "Ubuntu - Setting Up a Server."
date: 2011-07-03
forum: Server Platforms
---

### Post by Xirre on 2011-07-03
So I was thinking of making my own server. I make more than enough money to keep it up and It doesn't harm me not even the slightest. But I am wonder just how to do it though...

What I am basically trying to do are these steps on a WEBSITE of my own:

1. User signs-up (done) **i.e. XirreUser**

2. User verifies (done) **i.e. By verification code**

3. User logs-in (done)** i.e. at [http://xirre.atwebpages.com/login.php](http://xirre.atwebpages.com/login.php) [my website]**

4. User goes to Member Page (done) **i.e. at [http://xirre.atwebpages.com/members.php](http://xirre.atwebpages.com/members.php)**

5. User clicks Hosting Control Panel (help)** i.e. directs them to [http://xirre.atwebpages.com/members/hostcp.php](http://xirre.atwebpages.com/members/hostcp.php)**

6. User Clicks "Create New Host Folder" (help) **i.e. directs them to [http://xirre.atwebpages.com/members/hostcp/newfolder.php](http://xirre.atwebpages.com/members/hostcp/newfolder.php)**

7. User has a submit form where they can enter the name. {**Min 3 Characters and Max 25 Characters**} (help) **i.e. <form></form> & i.e. Name it LoAWFiles**

8. User directed to next page to CLICK browse and upload a file that is ONLY ".dmb" then click submit (help) **i.e. Uploads to [http://xirre.atwebpages.com/members/hostcp/](http://xirre.atwebpages.com/members/hostcp/)[Username]/[Folder Name]**

9. User directed to next page to CLICK browse and upload a file that is ONLY ".rsc" then click submit (help)** i.e. Uploads to the same directory as for .dmb**

10. User is directed in to their folder that they have created in the form of PHP {i.e. http://xirre.atwebpages.com/members/hostcp/XirreUser/LoAWFiles.php}, that shows both the .dmb file and .rsc file and has options at the top of the page that ask them the following:

[B]- Port # they want
- Settings they want (Trusted, Safe, Untrusted)
- Visibility (Public, Private, Invisible)[/B]

11. User clicks submit button and the site sends a message to my Ubuntu telling it to download from the website.** i.e. "wget http://xirre.atwebpages.com/members/hostcp/XirreUser/LoAWFiles/LoAW.dmb" & "wget http://xirre.atwebpages.com/members/hostcp/XirreUser/LoAWFiles/LoAW.rsc" or just "wget http://xirre.atwebpages.com/members/hostcp/XirreUser/LoAWFiles/" if that will download both files from there.**

12. The Ubuntu will then save it in a file by redirecting to **cd /Desktop/Xirre\ Server/XirreUser/LoAWFiles**

13. Still in that Folder, the Terminal will now run this command:

[B]DreamDaemon [yourgame].dmb [port] [options]

YourGame: The File name of the .dmb file
Port: The Port they have given from the sites <form>
Options: Settings and Visibility {Separated by spaces.}

i.e. DreamDaemon LoAW.dmb 4567 -trusted -public[/B]

14. User redirected to a different page that gives them their host link like so: **i.e. "byond://[Host IP]:[Server Port]" and listed on [http://xirre.atwebpages.com/members/hostcp/XirreUser/LoAWFiles/hostinfo.php](http://xirre.atwebpages.com/members/hostcp/XirreUser/LoAWFiles/hostinfo.php)**

15. The server is up and they are set to go.



This is the instructions on how to host. It would kind of give an idea on what should even be done: [here]("http://www.byond.com/members/LinuxGuild?command=view_post&post=109958").

If you need a reference of a site that has already performed this, ask. They performed it but they are crappy at prices and interface.

Edit: If anybody can do this and you would like to join our team then you may. We'd love to have somebody as skillful as this. If you don't want to join, please at least help us complete this project.

---

### Post by Xirre on 2011-07-03
Bump

---

### Post by tgalati4 on 2011-07-03
I think Drupal7 is up to the task.  It can do everything except running the DreamDaemon script.  That would be tricky because wouldn't the DreamDaemon need to run as root for each user?  Or can it work successfully running with user permissions?

Within Drupal, you have one website, but each user can have their own content page that they can control.  You can set levels of access control.  User pages could be public or private or viewable only by logged in (validated) "members".

And we like to reserve our b*mps for 24 hours.  Because this is a busy forum, your post might not get read by people for several hours.

---

### Post by Xirre on 2011-07-03
Isn't Drupal a Hosting Server with configs on it as well? I don't have my own domain. I have a subdomain for free with PHP, MySQL, etc on it. [http://xirre.atwebpages.com](http://xirre.atwebpages.com) - I mainly want to code in my own procedure. Though I can do most of them myself, I just don't know how to AUTOMATICALLY send info from my website to my Ubuntu to make Ubuntu start up automatically.


An idea: if somebody could tell me how to make an application, i'll probably look in to how to automate it so that I am the Owner of the Application and others can simply point and click on this application. I know a friend of mine who has created a BYOND Game like this. Though, the shell server isn't his. He pays for it.

I want to make an application where people can click browse and name their files and manage it. If this is harder than what I originally asked in my first post, i'll stick with my first post. If not, I'll move to applications then.

---

### Post by Xirre on 2011-07-03
Bump.

---

### Post by Xirre on 2011-07-03
Bump again. - Please help.. :/

---

### Post by Xirre on 2011-07-05
Bump.

---

### Post by Xirre on 2011-09-03
Bump again

---

### Post by Swashy on 2011-09-11
I've wanted to do something like this too as I have an extra machine, but I don't think I can be of much help as I suck at linux. However I think I can point you to some options.

Perhaps you could try installing [Freenas]("freenas.org") and then mess with it from there with an FTP type server? I would imagine it wouldn't be *too* advanced to setup or perhaps find a simple HTML database to overlay on top of it and then adding options into it.

[This article]("http://lifehacker.com/5822590/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-freenas") is what got me interested in this type of thing originally and it really doesn't seem like a huge leap to giving people login access through the internet. Unfortunately I myself haven't tried doing anything yet, too busy with school..

Good luck!

---

### Post by Xirre on 2012-04-07
Bump because I still need help. My new site is [http://xirre.com](http://xirre.com) - I am getting some payments and I know how to host it manually. But how can I make it so players can host it without me being at my computer? FTP, SSH, Putty, FileZilla, etc. Help? I don't completely know where to start nor do I know many commands.

---

### Post by lisati on 2012-04-07
*Thread moved to **Server Platforms**.*

---

### Post by JSunny on 2012-04-07
[http://xirre.atwebpages.com]("http://xirre.atwebpages.com/")

"There was an Malicious Attack" by Norton Internet Security

check our website please on malicious software by "teenhentaifiber.info"

prolly the ads...

---

