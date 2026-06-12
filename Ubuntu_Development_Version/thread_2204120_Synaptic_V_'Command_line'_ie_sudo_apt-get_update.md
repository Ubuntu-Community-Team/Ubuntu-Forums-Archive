---
title: "Synaptic V 'Command line' ie sudo apt-get update"
date: 2014-02-06
forum: Ubuntu Development Version
---

### Post by Hazzabin on 2014-02-06
opinions and "why" 

reason for asking is I've had mixed results using either one......but mostly serious issues updating via synaptic

so thought I would put the question to the "Guru's" here  :)

---

### Post by vasa1 on 2014-02-06
What is the question? And why Ubuntu+1 ?

---

### Post by Hazzabin on 2014-02-06
because all the issues I've currently had have been with 14.04, and YES I do know we are still in 'Alpha' or whatever they want to call it

and sorry, probably not so much a question, rather gathering opinions of people to which/why they prefer one way over another

---

### Post by Elfy on 2014-02-07
well I use the update manager now and again to check it works 

mostly I use a terminal but I do install synaptic in the first round of installing on any new install

I don't use the software centre thing

---

### Post by cariboo on 2014-02-07
I use synaptic due to shear laziness more than anything else. Once I have synaptic open, I only have to enter my password once, then leave it open for the rest of the session. No having to open a terminal and typing:

```
sudo apt-get update
```

and then typing:

```
apt-get upgrade
```

Three or four clicks, and I'm done. :-)

---

### Post by Buntu Bunny on 2014-02-07
I use the command line just to keep the commands fresh in my mind. I'm not a guru at CLI, but I like to do what I can.

---

### Post by vasa1 on 2014-02-07
@cariboo907, But isn't keeping Synaptic open (after signing in) then any different from having a gksudo nautilus window open? My understanding was that having GUI-based stuff running with root permission isn't something to be done lightly.

---

### Post by rrnbtter on 2014-02-07
Greetings,
I use the command line. I also use sudo with wreckless abandon. I've been installing and recovering various systems since the 80's so it doesn't matter to me what the results are. Only one reinstall on Trusty so far!

---

### Post by Hazzabin on 2014-02-07
Thanks guys for your answers, certainly seems a cross section, I guess "what suits you" is how you do it  :)

---

### Post by kurt18947 on 2014-02-07
> **cariboo907 said:**
> I use synaptic due to shear laziness more than anything else. Once I have synaptic open, I only have to enter my password once, then leave it open for the rest of the session. No having to open a terminal and typing:

```
sudo apt-get update
```

and then typing:

```
apt-get upgrade
```

Three or four clicks, and I'm done. :-)

Aren't you wearing your keyboard & fingers out needlessly?  ctrl-alt-t then up arrow until the commands come up?:cool:  Well, unless you're using terminal quite a lot. I tend to use Synaptic in the perhaps-mistaken belief that Synaptic does a better job of tracking changes than Update-Manager.  I don't know how apt-get compares.

---

### Post by 3rdalbum on 2014-02-08
> **Hazzabin said:**
> opinions and "why" 

reason for asking is I've had mixed results using either one......but mostly serious issues updating via synaptic

so thought I would put the question to the "Guru's" here  :)

"sudo apt-get upgrade" is a little more intelligent at resolving conflicts than just selecting all upgradable packages for installation.

Otherwise, Synaptic just does exactly what Apt-Get does. Use whatever suits you best in the situation. It will be rare to have one tool fail where the other succeeds.

---

### Post by grahammechanical on 2014-02-08
Synaptic, Software Updater and even Software Centre are just different Graphical User Interfaces for the apt-get commands. There is an advantage to using a terminal. It gives a bit more detailed information as to why an update or an install failed. Updating/installing through the terminal can be a useful diagnostic method.

Regards.

---

### Post by ajgreeny on 2014-02-08
I nearly always use synaptic which is the first package I install after full OS installation. so for that it's ```
sudo apt-get install synaptic
```  From then on I use synaptic, but in its preferences have it set to "Apply the changes in a terminal window" so it is easier to follow if there are any problems or warnings during the installation.

Synaptic is in my opinion a great deal easier to use for searching out details and properties of packages, and certainly a lot more flexible than the software-centre, which I can honestly say I have not used, not once, not ever, in the years that it has been available.  I started with synaptic in 2005 and have stayed with it ever since.

---

### Post by Hazzabin on 2014-02-08
Once again thanks guys for the replies/answers/suggestions

well one learns something new everyday "[COLOR=#000000]set to "Apply the changes in a terminal window" so it is easier to follow"

thanks [/COLOR][COLOR=#000000]ajgreeny, I did not know of this[/COLOR][COLOR=#000000]





[/COLOR]

---

### Post by cariboo on 2014-02-08
One major benefit I've found using synaptic,  for me it is much easier to find and remove broken packages using the broken package filter.

---

### Post by kurt18947 on 2014-02-10
I have seen one apparent benefit of terminal commands over the software updater.  In the past I've seen the "Would you like to perform a partial upgrade?" message. Thanks but no.  Exit the updater, launch a terminal run the commands and nothing about partial upgrades, no broken system.  I've not seen partial upgrade offers during the past couple cycles but then I seldom use the software updater.

---

### Post by Cavsfan on 2014-02-11
I *only* use the terminal commands and sometimes use Synaptic to look at the change log, etc. or other detailed information. Although I do use Synaptic to install packages just not get updates.
But instead of typing all of those command out I just enter **ud** in terminal and my password. 
After that is finished if there were any packages held back I enter **ud2** to get the updated packages and the new ones that come with it. 
If there is anything still held back I just wait until the dependencies are complete or whatever and then the updates comes through.

(Pardon if you've seen this before as I've mentioned it before.)  
I make aliases of **ud** and **ud2** and also **ud3** to do a **sudo apt-get autoremove** like this: Edit the .bashrc file **gedit ~/.bashrc** and add the blue lines below the other lines.
Save it and logout and back in and they will then work. Saves on typing all those commands over and over again. 

```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

[COLOR=#0000ff]# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
alias ud3='sudo apt-get autoremove'[/COLOR]

```

---

### Post by cariboo on 2014-02-11
@Cavsfan, you can use apt-get to view change logs:

```
apt-get changelog gnome-panel
```

for instance gets you the gnome-panel changelog.

```
apt-get changelog <packagename>
```

will get you the changelog for any package, if it is available.

---

### Post by Cavsfan on 2014-02-12
> **cariboo907 said:**
> @Cavsfan, you can use apt-get to view change logs:

```
apt-get changelog gnome-panel
```

for instance gets you the gnome-panel changelog.

```
apt-get changelog <packagename>
```

will get you the changelog for any package, if it is available.

Thanks for that information I didn't know apt-get could do that. I was aware of what **apt-cache policy <packagename>** does. but not this.
That's one more thing that I will not need Synaptic for any more. That is one of the main reasons I even used Synaptic other than to look at file dependencies. 

Pretty sweet thanks again for that! :popcorn:

---

### Post by Cavsfan on 2014-02-14
> **cariboo907 said:**
> @Cavsfan, you can use apt-get to view change logs:

```
apt-get changelog gnome-panel
```

for instance gets you the gnome-panel changelog.

```
apt-get changelog <packagename>
```

will get you the changelog for any package, if it is available.

@cariboo907 What I noticed that was especially cool about that is that you just have to click on the bugs that that version fixes and open it up in a browser.
I thought I was going to have to search for the bug until I put my mouse over the bug and viola! :D

---

### Post by Cavsfan on 2014-02-25
> **vasa1 said:**
> @cariboo907, But isn't keeping Synaptic open (after signing in) then any different from having a gksudo nautilus window open? My understanding was that having GUI-based stuff running with root permission isn't something to be done lightly.

Vasa1, they are totally different. Synaptic has nothing to do with sudo or gksudo. It is just a powerful app that can do several things. It asks for your password before you can do anything.
You usually do not have Synaptic open for very long; just long enough to do whatever you were needing to do. 

A gksudo nautilus window would be a totally different animal with nothing to do with upgrading, installing, etc.

---

### Post by cariboo on 2014-02-25
> **vasa1 said:**
> @cariboo907, But isn't keeping Synaptic open (after signing in) then any different from having a gksudo nautilus window open? My understanding was that having GUI-based stuff running with root permission isn't something to be done lightly.

It could possibly be a problem, if some random user could discover my lock screen password, but all of my family won't even think of touching my main computer system, as I have a system set up for guest usage.

I do get bitten on occasion, when I try to install something from the command line with synaptic still open.

---

### Post by Cavsfan on 2014-02-25
> **cariboo907 said:**
> I do get bitten on occasion, when I try to install something from the command line with synaptic still open.

Are you talking about this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

I get that once in a while without synaptic open. I think update-manager is trying to open. I just open update-manager and then close it and the error goes away.

---

### Post by cariboo on 2014-02-25
> **Cavsfan said:**
> Are you talking about this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

I get that once in a while without synaptic open. I think update-manager is trying to open. I just open update-manager and then close it and the error goes away.

That's exactly the error I get. :)

---

