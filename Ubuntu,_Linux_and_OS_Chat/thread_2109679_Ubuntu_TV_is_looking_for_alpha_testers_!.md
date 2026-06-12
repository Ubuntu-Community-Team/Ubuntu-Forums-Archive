---
title: "Ubuntu TV is looking for alpha testers !"
date: 2013-01-28
forum: Ubuntu, Linux and OS Chat
---

### Post by josephmills on 2013-01-28
Hello there to all. We are happy to be able to tell all of you that there is active development on Ubuntu TV. 

If you would like to help out With Ubuntu TV please feel free to look at are Bleeding edge ppa. (It builds daily)
[https://launchpad.net/~u2t/+archive/bleedingedge](https://launchpad.net/~u2t/+archive/bleedingedge)

How to install 
What you are going to need

518 mb ram (**2gigs** or more recommended esp if you want to use **opengl**)

A p4 or something like that or better (if you are running vbox I am sure you have a p4 or some cpu that is higher and better then that , again opengl)

Recommended: 
      mythtv 0.26 (a myth backend also ) 
      unity-lens-mythtv  
      unity-lens-news 
& any other lens that you like. 
make a virtual machine (best for now) install Ubuntu 12.04
then 
```

sudo add-apt-repository ppa:u2t/bleedingedge
sudo apt-get update
sudo apt-get install unity-2d

```


How to start the TV 
[https://plus.google.com/u/0/104659991254860976283/posts/H5GKRE3ja2w](https://plus.google.com/u/0/104659991254860976283/posts/H5GKRE3ja2w)


Place to file all bugs
[https://bugs.launchpad.net/u2t](https://bugs.launchpad.net/u2t)


I note from Developers 

> 
Many of you know that I (Joseph Mills (bobweaver)) have been working on this. I think that when the phone code comes out I will start porting more and more of this over to the Phone ,  But if you want to try this out feel free. 

If you would like to hack on this there is many many fix me tags  in the code. (esp in the shell.qml )
 
I will also be putting more things on the blueprints of launchpad. 

This code only works on 12.04 there is NO plans for me to move this code up to anything else then 12.04. Because when the phone code goes public. I will be porting this over to that. So there is no point in re-writing libunity libdee or anyof that. When the phone uses qml also. Once the public gets the Phone code We will be able to go through that and look to see how they are reading/rendering lens and filters and all that stuff.Then integrate the older code to match this.




Some things that we are going to be working on in the next week. Feel free to help if you like. 

armel and ppc weekly builds
get ready to port to qt5 
set up to run on mutter and not metacity 
make custom theme for mutter
there are also lists of bugs on lp and blueprints


are social Pages 
Google Plus 
[https://plus.google.com/u/0/b/104659991254860976283/](https://plus.google.com/u/0/b/104659991254860976283/)

Are Facebook 
[http://www.facebook.com/UbuntuTV](http://www.facebook.com/UbuntuTV)

Are Twitter 
[https://twitter.com/TVUbuntu](https://twitter.com/TVUbuntu)

Are Wiki (needs to be updated** REAL BAD** )
[https://wiki.ubuntu.com/UbuntuTV/Contributing](https://wiki.ubuntu.com/UbuntuTV/Contributing)

Ubuntu Home page for TV 
[http://www.ubuntu.com/devices/tv](http://www.ubuntu.com/devices/tv)


Joseph's youtube channel 
[http://www.youtube.com/user/mrbobweaver?feature=mhee](http://www.youtube.com/user/mrbobweaver?feature=mhee)

> Do we have a IRC channel ?  

yes we have 2 on freenode 
(for developers) #u2t
(for general questions) #ubuntu-tv


[img]https://lh4.googleusercontent.com/-UphuSwbAHq8/UQOSCla6rII/AAAAAAAAAIk/gTodQw2KwXw/w497-h373/Screenshot%2Bfrom%2B2013-01-26%2B03%253A17%253A46.png[/img]

---

### Post by eriktheblu on 2013-01-28
I'll give it a try. My Mythbuntu box is only occupied as a Minecraft server right now.

---

### Post by johnkjaer on 2013-02-26
Going for it
but will be missing LIRC

Update:
When i login with ubuntu 2d and press the ubuntu button.

[FONT=arial][SIZE=2][COLOR=#333333]Then I try to push the "gear button" nothing happens. I'm trying to change into "tv mode"[/COLOR][COLOR=#333333].
[/COLOR][/SIZE][/FONT]
Any solutions?

To many bugs, i am out.

---

### Post by Rokkross on 2013-02-26
Awesome! I was convinced that this project was completely dead. I didn't look into it much, though.

Is commercial release still a plan for Ubuntu TV? I imagine that convincing manufacturers to load this on their machines is incredibly difficult, but have you guys given up?

---

### Post by grahammechanical on 2013-02-27
>  ubuntu 2d.

is Unity 2D. Ubuntu = Unity = Ubuntu. So, Ubuntu 2D = Unity 2D. And by the way, Ubuntu 12.10 onwards does not have Ubuntu/Unity 2D. That is why it is recommended to test Ubuntu TV on 12.04.

Regards.

---

### Post by grahammechanical on 2013-02-27
>  ubuntu 2d.

is Unity 2D. Ubuntu = Unity = Ubuntu. So, Ubuntu 2D = Unity 2D. And by the way, Ubuntu 12.10 onwards does not have Ubuntu/Unity 2D. That is why it is recommended to test Ubuntu TV on 12.04.

Regards.

---

### Post by Rokkross on 2013-02-27
> **grahammechanical said:**
> is Unity 2D. Ubuntu = Unity = Ubuntu. So, Ubuntu 2D = Unity 2D. 
No, I'm pretty sure Unity = Ubuntu = Linux = RedHat = Linux = Oracle Linux.

We should be testing this on Oracle Linux.

---

### Post by nights815 on 2013-03-28
> **johnkjaer said:**
> Going for it
but will be missing LIRC

Update:
When i login with ubuntu 2d and press the ubuntu button.

[FONT=arial][SIZE=2][COLOR=#333333]Then I try to push the "gear button" nothing happens. I'm trying to change into "tv mode"[/COLOR][COLOR=#333333].
[/COLOR][/SIZE][/FONT]
Any solutions?

I also am seeing this problem.
Using Virtual box 4.2.6
Attempted this on 2 fresh installs using 12.04.1 and 12.04.2  (32bit)
After logging in with Unity 2d The launcher hides to the left. Super key unhides it temporarly enough to click on dash.
Settings shows a blank menu. (no option to go to "tv mode" as seen in the google plus video)
Later today I will try a fresh install on my laptop and attempt this with 12.04.00 thru 12.04.2 (just for fun) to see if virtual box is the issue.

---

