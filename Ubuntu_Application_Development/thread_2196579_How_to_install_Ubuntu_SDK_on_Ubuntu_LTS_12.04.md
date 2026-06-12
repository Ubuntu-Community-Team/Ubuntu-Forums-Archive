---
title: "How to install Ubuntu SDK on Ubuntu LTS 12.04"
date: 2013-12-30
forum: Ubuntu Application Development
---

### Post by hasanarbab2 on 2013-12-30
Hi,
I have tried like everything. can someone please help me out on installing ubuntu sdk.

in terminal i used as instructed "sudo apt-get install ubuntu-sdk"

Output was: 
"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ubuntu-sdk : Depends: qtcreator-plugin-ubuntu-cordova but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
"

when try to install qtcreator-plugin-ubuntu-cordova separately, I get 
"
sudo apt-get install qtcreator-plugin-ubuntu-cordova
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 qtcreator-plugin-ubuntu-cordova : Depends: qtcreator-plugin-ubuntu (= 2.8.1bzr56precise0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
"

Please Help, i am unable to find a way out.

---

### Post by dsc1596 on 2013-12-30
Try running "sudo apt-get update && sudo apt-get dist-upgrade" if you haven't already, and if that gives errors, then try "sudo apt-get install -f". This will fix any dependencies that haven't been resolved with your current configuration. When you get the error "E: Unable to correct problems, you have held broken packages." that may mean you need to resolve some dependencies. you may also want to check out [this thread.]("http://askubuntu.com/questions/363200/e-unable-to-correct-problems-you-have-held-broken-packages")

---

### Post by hasanarbab2 on 2013-12-31
thanks dsc1596. the command which I used at very first was "sudo add-apt-repository ppa:ubuntu-sdk-team/ppa && sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install ubuntu-sdk". you can see it covers ppa addition, update and dist-upgrade. this was the installation way they suggested on ubuntu sdk page. I tried -f as u suggest but it does not help at all. then i read ur provided link. this is actually about conflicted packages. and method given there does not help too as i do not have any held are conflicting package.

I actually want to learn programming for ubuntu. so please, could u or anyone else find me another way, that would really be appreciated.

---

### Post by kajoky on 2013-12-31
Have you tried programming in c or c++?
The compiler and a text editor are already installed.
If you are really wanting to work with QT then QtCreator may be the way to go.
I have done a little programming with c.

---

### Post by kajoky on 2013-12-31
I tried via the GUI method.
I went to Software Center
Clicked on Developer Tools
Scrolling down I found QtCreator and clicked that.
On the next page I scrolled down to Add-ons and put a check by Ubuntu SDK.
Scrolled back up and clicked install.
It appears to have worked....
I have Ubuntu 12.04 LTS

---

### Post by dsc1596 on 2013-12-31
Well, in your original post you had output from the terminal that said "E: Unable to correct problems, you have held broken packages." that makes me think that you have some package issues that need to be resolved. Personally I would remove the ppa, and then update completely using the following code, each command one at a time, so you can really see what is going on more easily:
```

sudo add-apt-repository --remove ppa:ubuntu-sdk-team/ppa
sudo apt-get update
sudo apt-get dist-upgrade

```

If the above completes with no errors or other messages about broken packages, then you should be all set. Since you are doing a dist-upgrade however, it may be a good idea to restart as well using "sudo shutdown -r now" (without quotes) in case something major was upgraded like your kernel or display-related packages. 
Then try to install the SDK ppa again with the commands you used originally.

If that doesn't fix the problem, then try the following:

```
dpkg --get-selections | grep hold
```

This will list the packages that are being held. Please post the results here, and we can move on from there. Just for reference purposes, the above code is from [this post.]("http://askubuntu.com/questions/223237/unable-to-correct-problems-you-have-held-broken-packages")

---

### Post by viswaprasath on 2014-01-07
When i install from Ubuntu Software center.. i get following message. i have ubuntu installed freshly 12.04 oly.
And the recommended updates are done. Nothing works..

Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

ubuntu-sdk:

---

### Post by ||0BL1v10N|| on 2014-02-02
Hey man,

Thanks very much! Fixed the problem. When I rebooted it told me that the software centre wasn't working but I updated the packages again and it is working! 

Thanks, Niall

---

