---
title: "Funny File Permissions"
date: 2014-10-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Crazy_Raisin on 2014-10-19
I am not a new user of Linux, in fact I have been these boards before but can't sign in. It has been a while since I have used Ubuntu Desktop version, I have mainly been sticking with CentOS for server purposes. But recently I was given a CF card and was asked if I could copy the contents, ideally into an image format so if necessary other CF cards can be copied over in case there is some system issue and they need to replace the card.

Maybe I made a mistake in here somewhere but the entire process was a nightmare and made me think why put all this effort in designing a sleek new UI if semi difficult tasks are made more difficult?

For this purpose I tried sticking with UI only, I am on one a desktop version of Ubuntu so why should I use the terminal?

Anyways, when copying the files I get an error saying that I do not have the permissions as I am root, well that makes sense, no problem so I look into the properties and I get this (see attached image).

Not being able to copy the files because I am not root makes sense but then what does not make sense is that there is no option to enter the root password and change the permissions so then you would be able to copy them over. And yes I know of CHMOD and all that through the terminal but I am talking about the GUI aspect here.

Well searching on the internet I come across and article that says that Ubuntu allows you to create administrator accounts (did not specify if these are accessible root accounts or just accounts they called "administrator") but they warned against it.So I did it anyway and tried copying the files again thinking now that I am administrator I must be able to have access to all the files, well no, same problem, no permission.

So this is one of the things I found frustrating with the desktop versions of Linux (all the different distros) is that you are constantly having to refer back to the terminal because some function is missing in the GUI. Again I  can be completely mistaken here but I don't really need a reason why couldn't there be a button allowing someone to enter the root password and be able to change the permissions and copy of the files?

Long story, I ended up making an image of the of the CF card on a Windows computer using a software that provided support for Ext 3 and 4. This literally took me 10 minutes to setup (not including the time to make the image as it was several gigabytes and took a while).

The last time I have used Ubuntu Desktop version was version and I still find numerous times having to use the terminal to get certain things done since that version of whatever function was missing in the GUI design.

So what is the point of making such nice looking GUI's and graphics if most of the time you expect the user to be using the terminal?

Lastly, this is probably going to bring out a lot of the zealots but seeing there are different versions of Ubuntu out there like Xubuntu, Lubuntu, etc why not just provide a fork that follows the GoboLinux file system model? The backwards capability works pretty well, there are issues obviously but they are fixable and it does not become a completely nightmare for those who don't just use the computer to look at funny cat pictures.

---

### Post by Bucky Ball on 2014-10-20
*Thread moved to **General Help**.*

Welcome. Easiest? Open a terminal (even though you don't see why you should have to) and:

```
gksudo nautilus
```

You have a file manager open as root.

You have posted a lot of general thoughts regarding Ubuntu in a support thread. Please try and keep them separate. You originally posted in a support area. Post comment and opinion in The Cafe or one of the other non-support areas, please. I have also attached your large pic. Please do this in future and spare a thought for those with slow connections or vision issues. Thanks.

Images can be attached using 'Go Advanced' or 'Adv Reply' and use the paperclip icon. 

Good luck.

---

### Post by Crazy_Raisin on 2014-10-20
I apologize if I posted incorrect, I guess then this would be more of a support type of deal?

The thing though that I had created an administrator account (which I assume is root), accessed and still had no permissions and could not change the permissions. Running the file manager like you can in Windows "right and select 'Run as Administrator'" is not an option.

---

### Post by yancek on 2014-10-20
If you want details on how this works in Ubuntu, the sudo thing, read the link below.
Most Linux distributions require that during the installation one creates a 'normal' user without privileges and also create a password for the root user.  With Ubuntu and a number of other distributions this is not done.  During the installation, you are required to create one user and create a password for that user.  When that user logs in, s/he is a normal user and needs to gain root privileges by using sudo prefixed to a command or as pointed out above, use gksudo nautilus to open a file manager with root privileges.  

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by deadflowr on 2014-10-20
Did you ever get around to actually install Ubuntu?
Your screenie is of a live session.
User permissions based on the groups a user belongs to differ from a true install and a live session.

---

### Post by nerdtron on 2014-10-20
I read this post earlier. It almost turned on my "grumpy mode". But then again, I calmed myself as this post is just a troll of someone who hasn't explored the OS yet. 
I have used both Ubuntu Desktop and Server and currently CentOS and Red Hat servers. Yes they have diferrences, and yes some are annoying but I don't think Ubuntu is inferior in this regard. 

They both have different audience and purpose and they do their jobs.

---

### Post by mastablasta on 2014-10-21
> **Crazy_Raisin said:**
> 
For this purpose I tried sticking with UI only, I am on one a desktop version of Ubuntu so why should I use the terminal?

there should be a shortcut that is something like Nautilus (root) - clicking on that would get you "root" access to file manager. as mentioned sudo is used in Ubuntu and things are done differently than in CentOS.

khm speaking dropping to command line... how does one configure software raid in centos 6 instali ;)  :P

> 
Lastly, this is probably going to bring out a lot of the zealots but seeing there are different versions of Ubuntu out there like Xubuntu, Lubuntu, etc why not just provide a fork that follows the GoboLinux file system model? The backwards capability works pretty well, there are issues obviously but they are fixable and it does not become a completely nightmare for those who don't just use the computer to look at funny cat pictures.

Ubuntu is provided by Cannonical (before Kubuntu was made by them as well). Other distributions are Community Editions but they are also official distros. Kubuntu is sponsored by Blue Systems for example.

Kind of but not exactly like RHEL is provided by Red Hat and CenOS, Scientific Linux are provided by community. Only RHEL is charging for some addons. While Ubuntu is charging separately for some server addons. While desktop is free.

As I understand GoboLinux is still at an experimental stage and not considered something that could be used in production environment (i.e. businesses). I am sure that if they manage to resolve issues with such packaging there might be more distros switching to that model.

---

### Post by Crazy_Raisin on 2014-10-22
> Easiest? Open a terminal (even though you don't see why you should have to) and:


My point or guess what I found odd is that why go through the energy of designing of neat looking UI if anything moderately complicated requires terminal in order for it to be the easiest and quickest route? Let's just forget quickest, easiest.


In Windows you can right click and click a button to enter the administrator's password (if you got it), it is the same thing in terms of security but less complicated.


So essentially it comes down to this: Here is a nice looking UI we took a lot of effort and time to design and it is easy to use only if you are looking on the internet for pictures of cats and checking your email.


I don't get that mindset.


> Most Linux distributions require that during the installation one creates a 'normal' user without privileges and also create a password for the root user. With Ubuntu and a number of other distributions this is not done. During the installation, you are required to create one user and create a password for that user. When that user logs in, s/he is a normal user and needs to gain root privileges by using sudo prefixed to a command or as pointed out above, use gksudo nautilus to open a file manager with root privileges. 


I know why it is done, what I don't get is why a distro that has a nice looking UI is still requiring this security feature to be done through a terminal instead of a GUI aspect. That's all.


> Did you ever get around to actually install Ubuntu?


No I just dropped it. I just needed to make a copy of the files which I did on Windows using free and paid applications.


> I read this post earlier. It almost turned on my "grumpy mode". But then again, I calmed myself as this post is just a troll of someone who hasn't explored the OS yet.


CONGRATULATIONS! You are the first Linux zealot.


> They both have different audience and purpose and they do their jobs.


Re-read what I wrote instead of turning your "grumpy mode" on and off.


> there should be a shortcut that is something like Nautilus (root) - clicking on that would get you "root" access to file manager. as mentioned sudo is used in Ubuntu and things are done differently than in CentOS.


Why is everyone so attached to CentOS? I only mentioned to point out I am not new to Linux. I am just pointing out that it is strange how you have to use the terminal to get around file permissions while you have this nice looking UI in Ubuntu. That's all.

My whole entire point has been this: Ubuntu has a nice new UI but even moderately difficult items are almost required to be done through terminal which makes no sense.  You can have the same security in UI if willing.

---

### Post by deadflowr on 2014-10-22
My point stands.
There is a big difference in user functions in a live session than an installed session.

If you want to run live sessions and have full capabilities, then perhaps a single user live cd system like puppy linux would be more apt for you.

---

### Post by Bucky Ball on 2014-10-22
*Thread moved to **Ubuntu, Linux and OS Chat**.*

See [HERE]("http://linux.oneandoneis2.org/LNW.htm").

If you want support with Ubuntu please post a thread with a descriptive title in the appropriate support area. This is the place if you want to debate the pros and cons.

---

### Post by mastablasta on 2014-10-23
> **Crazy_Raisin said:**
> 
Why is everyone so attached to CentOS? I only mentioned to point out I am not new to Linux. I am just pointing out that it is strange how you have to use the terminal to get around file permissions while you have this nice looking UI in Ubuntu. That's all.


re-read again what i wrote and oyu you do things via GUI.

Furthermore Gnome (and Unity) deliberatelly "hide" advanced features from users as to not overwhelm them with settings in GUI. KDE on the other hand has many advanced settings things done via GUI.

having said that - I should repeat that for the stuff you want to do you do not have to drop into terminal as you claim.

I am a fan of GUI myself as my keyboard is often pushed forward and I am often using mouse only. also i have enough typing at work... so I do know there is a GUI for most things. even for servers...

on the other hand dropping to terminal does make users think a bit more as opposed to clicking around or running as administrator the whole time, deleting system files etc.

---

### Post by Crazy_Raisin on 2014-10-23
> **deadflowr said:**
> My point stands.
There is a big difference in user functions in a live session than an installed session.

If you want to run live sessions and have full capabilities, then perhaps a single user live cd system like puppy linux would be more apt for you.

Alright then I will install Ubuntu on one of my empty computers and recreate this scenario as again.

---

### Post by Crazy_Raisin on 2014-10-23
> **mastablasta said:**
> re-read again what i wrote and oyu you do things via GUI.

Furthermore Gnome (and Unity) deliberatelly "hide" advanced features from users as to not overwhelm them with settings in GUI. KDE on the other hand has many advanced settings things done via GUI.

having said that - I should repeat that for the stuff you want to do you do not have to drop into terminal as you claim.

I am a fan of GUI myself as my keyboard is often pushed forward and I am often using mouse only. also i have enough typing at work... so I do know there is a GUI for most things. even for servers...

on the other hand dropping to terminal does make users think a bit more as opposed to clicking around or running as administrator the whole time, deleting system files etc.

I will install Ubuntu on one of my empty computers and try this again.

---

### Post by Crazy_Raisin on 2014-10-23
> **Bucky Ball said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*

See [HERE]("http://linux.oneandoneis2.org/LNW.htm").

If you want support with Ubuntu please post a thread with a descriptive title in the appropriate support area. This is the place if you want to debate the pros and cons.

What is your point with that link? From the very start i stated that I have knowledge of Linux, I work with Linux I just have not worked with Ubuntu as much before so I may be incorrect in some of my complaints. 

But my point stands as well, if you are going to make a nice looking UI then reduce the terminal use next to 0.

---

### Post by /ADM on 2014-10-23
If you have knowledge and have worked with Linux then what is the problem of using the terminal?  Just wondering..

Take a look at how Windows has evolved.  Ever used Windows 95?  Half the stuff that was technical needed the cmd prompt.  It's only since XP was released that nearly all programs that used the prompt were converted into GUI apps.  However this costs time and money.

So have some patience, it's free.

---

### Post by mastablasta on 2014-10-25
heh... [http://kde-look.org/content/show.php?action=content&content=48411](http://kde-look.org/content/show.php?action=content&content=48411)

also no need for terminal ... Atlf=f2 and "kdesudo dolphin" will run it as root

---

