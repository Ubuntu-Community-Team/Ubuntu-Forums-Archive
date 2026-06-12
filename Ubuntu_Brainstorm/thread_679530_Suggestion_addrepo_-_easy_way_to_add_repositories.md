---
title: "Suggestion: addrepo - easy way to add repositories"
date: 2008-01-27
forum: Ubuntu Brainstorm
---

### Post by buu700 on 2008-01-27
Hi. I wrote a simple BASH program, which I think would be really useful for inclusion in Hardy.

I describe it in detail here: [http://ubuntuforums.org/showthread.php?p=4214665#post4214665](http://ubuntuforums.org/showthread.php?p=4214665#post4214665)

> **buu700 said:**
> Hi. I promise I'll release Macbuntu soon...

Anyways, while I was working on Macbuntu, I wrote this really useful BASH script I'm including that I think everyone could benefit from. It's called 'addrepo,' Basically, it just makes the adding of new repositories *extremely* simple. Here's the output if you run it without any arguments, which explains how to use it:

buu700@Canada:~$ addrepo 
addrepo is a simple command line interface for easily adding APT repositories to your sources.list
Usage: addrepo [repository]
buu700@Canada:~$ 

Then of course you just replace '[repository]' with a repository name (e.g. addrepo deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free). It already includes 'sudo,' so adding sudo before you enter the command is not necessary.

To add this script to your current system, just run the following commands:

sudo wget [http://mac4deb.googlepages.com/addrepo](http://mac4deb.googlepages.com/addrepo) -O /usr/bin/addrepo
sudo chmod +x /usr/bin/addrepo

Just figured that everyone else may as well have the option of using that. (Oh, and I guess I'll also see if the Ubuntu devs would like to include this in Hardy by default.)


EDIT:
[http://www.digg.com/linux_unix/Addrepo_the_easiest_way_to_add_APT_repositories](http://www.digg.com/linux_unix/Addrepo_the_easiest_way_to_add_APT_repositories)
[http://reddit.com/info/66r2i/comments/](http://reddit.com/info/66r2i/comments/)
[http://www.ubuntugeek.com/addrepo-easiest-way-to-add-apt-repositories.html](http://www.ubuntugeek.com/addrepo-easiest-way-to-add-apt-repositories.html)

If you don't feel like downloading the file to read the code (I only go up to 100 potential arguments because realistically no repository will have nearly that many anyways):

```
#!/bin/bash
if [ $# -lt 1 ]; then
echo -e "addrepo is a simple command line interface for easily adding APT repositories to your sources.list\nUsage: addrepo [repository]"
else
if [ -e /tmp/addrepo.tmp ]; then
sudo mv /tmp/addrepo.tmp /tmp/addrepo.tmp.bak
fi
sudo echo $1 >> /tmp/addrepo.tmp
if grep -q "deb" /tmp/addrepo.tmp; then
echo "" | sudo tee -a /etc/apt/sources.list
numbers=(${0} ${1} ${2} ${3} ${4} ${5} ${6} ${7} ${8} ${9} ${10} ${11} ${12} ${13} ${14} ${15} ${16} ${17} ${18} ${19} ${20} ${21} ${22} ${23} ${24} ${25} ${26} ${27} ${28} ${29} ${30} ${31} ${32} ${33} ${34} ${35} ${36} ${37} ${38} ${39} ${40} ${41} ${42} ${43} ${44} ${45} ${46} ${47} ${48} ${49} ${50} ${51} ${52} ${53} ${54} ${55} ${56} ${57} ${58} ${59} ${60} ${61} ${62} ${63} ${64} ${65} ${66} ${67} ${68} ${69} ${70} ${71} ${72} ${73} ${74} ${75} ${76} ${77} ${78} ${79} ${80} ${81} ${82} ${83} ${84} ${85} ${86} ${87} ${88} ${89} ${90} ${91} ${92} ${93} ${94} ${95} ${96} ${97} ${98} ${99} ${100})
for ((i=1;i<=$#;i+=1)); do
echo -n "${numbers[$i]} " | sudo tee -a /etc/apt/sources.list
done
echo -e "\nRepository successfully added."
else
echo -e "\nNot a valid repository."
fi
sudo rm /tmp/addrepo.tmp
fi
```

---

### Post by Sanjay on 2008-01-27
Perhaps integrate zenity dialogs.... then you could just have a launcher on a panel that points to the script, zenity powered dialog box pops up, you give it the repo line, and repo is added, easy peasy?

---

### Post by MadMan2k on 2008-01-27
apturl already does that...

---

### Post by Martje_001 on 2008-01-27
And 'Software Sources' in 'Administration' -.-

---

### Post by patrickfromspain on 2008-01-27
I like the Software sources tool...

---

### Post by buu700 on 2008-01-27
> **Sanjay said:**
> Perhaps integrate zenity dialogs.... then you could just have a launcher on a panel that points to the script, zenity powered dialog box pops up, you give it the repo line, and repo is added, easy peasy?

Okay. Taking Sanjay's advice, I just quickly wrote an alternate version called 'gkrepo.' Basically, it does the same thing as addrepo, but uses gksudo and some zenity dialogs.

If gkrepo is entered without any arguments, it will prompt for a repository name. If gkrepo is entered with arguments, it will assume that the given arguments are the repository name. If not, a zenity dialog will prompt for the name. Afterwards, it will verify whether or not the repository name entered is valid (whether or not it begins with "deb"). If the repository name is valid, it will use gksudo to prompt fro a password, add the repository to the user's sources.list file, and notify the user that the repository has been added.

To add gkrepo to your current system, just enter the following commands:

sudo wget [http://mac4deb.googlepages.com/gkrepo](http://mac4deb.googlepages.com/gkrepo) -O /usr/bin/gkrepo
sudo chmod +x /usr/bin/gkrepo

Here is the source rode for gkrepo:
```
#!/bin/bash


#Dialog prompting for repository if none is entered

if [ $# -lt 1 ]; then
REPOSITORY=$(zenity --entry --title=gkrepo --text="Enter the name of the repository you would like to add below:")
gksudo root
if [ -e /tmp/gkrepo.tmp ]; then
sudo mv /tmp/gkrepo.tmp /tmp/gkrepo.tmp.bak
fi
sudo echo $REPOSITORY >> /tmp/gkrepo.tmp
if grep -q "deb" /tmp/gkrepo.tmp; then
echo "$REPOSITORY" | sudo tee -a /etc/apt/sources.list
zenity --info --title=gkrepo --text="Repository successfully added."
else
zenity --info --title=gkrepo --text="Not a valid repository. gkrepo aborted."
fi


#Adds repository if one is entered

else
gksudo root
if [ -e /tmp/gkrepo.tmp ]; then
sudo mv /tmp/gkrepo.tmp /tmp/gkrepo.tmp.bak
fi
sudo echo $1 >> /tmp/gkrepo.tmp
if grep -q "deb" /tmp/gkrepo.tmp; then
echo "" | sudo tee -a /etc/apt/sources.list
numbers=(${0} ${1} ${2} ${3} ${4} ${5} ${6} ${7} ${8} ${9} ${10} ${11} ${12} ${13} ${14} ${15} ${16} ${17} ${18} ${19} ${20} ${21} ${22} ${23} ${24} ${25} ${26} ${27} ${28} ${29} ${30} ${31} ${32} ${33} ${34} ${35} ${36} ${37} ${38} ${39} ${40} ${41} ${42} ${43} ${44} ${45} ${46} ${47} ${48} ${49} ${50} ${51} ${52} ${53} ${54} ${55} ${56} ${57} ${58} ${59} ${60} ${61} ${62} ${63} ${64} ${65} ${66} ${67} ${68} ${69} ${70} ${71} ${72} ${73} ${74} ${75} ${76} ${77} ${78} ${79} ${80} ${81} ${82} ${83} ${84} ${85} ${86} ${87} ${88} ${89} ${90} ${91} ${92} ${93} ${94} ${95} ${96} ${97} ${98} ${99} ${100})
for ((i=1;i<=$#;i+=1)); do
echo -n "${numbers[$i]} " | sudo tee -a /etc/apt/sources.list
done
echo ""
zenity --info --title=gkrepo --text="Repository successfully added."
else
zenity --info --title=gkrepo --text="Not a valid repository. gkrepo aborted."
fi
fi
sudo rm /tmp/gkrepo.tmp
```

---

### Post by buu700 on 2008-01-30
Here are some screenshots of gkrepo.

---

### Post by chacham23 on 2008-01-30
Nice program.. thanks m8 :)

---

### Post by smartboyathome on 2008-01-30
> **MadMan2k said:**
> apturl already does that...

Though wasn't this functionality disabled in Gutsy's apturl?

---

### Post by lexen on 2008-01-30
I think we should have this program in Hardy.  I don't see much use for the gui, we can already do that easily enough, but being able to add a repository simply by typing addrepo then the repository could save a lot of time.  How big is the program, because I know that space is a big issue when it comes to what programs will be shipped with Ubuntu.



P.S.  Where can I get Macbuntu?  It sounds interesting.  Is there a way to install just the desktop along with ubuntu?

Thanks,
Lexen

---

### Post by buu700 on 2008-01-30
> **lexen said:**
> I think we should have this program in Hardy.  I don't see much use for the gui, we can already do that easily enough, but being able to add a repository simply by typing addrepo then the repository could save a lot of time.  How big is the program, because I know that space is a big issue when it comes to what programs will be shipped with Ubuntu.



P.S.  Where can I get Macbuntu?  It sounds interesting.  Is there a way to install just the desktop along with ubuntu?

Thanks,
Lexen

Glad you like it! Normal command line addrepo is 1.2 KB, and gkrepo is 1.7 KB. About the command line one being more useful, actually, while I do agree it would be faster if I were already in a terminal, the graphical version (gkrepo) is potentially MUCH faster than either addrepo or the GUI that defaultly comes with Ubuntu if you use it effectively. (i.e. you could have a keyboard shortcut set to run gkrepo. Then, you would just press your assigned shortcut, paste the repository name into the zenity dialog that pops up, enter your password into tho gksudo dialog that pops up, and you're done!)
About Macbuntu, I'm still working on it, so you can't get it now, but when it's done you will be able to install it on top of an existing Xubuntu installation with a BASH script, but a fresh install would be recommended.

---

### Post by smartboyathome on 2008-01-30
Wouldn't it be just as good to enable the repo-adding feature in apturl as well? I am all for it, but it seems the devs are convinced that it could lead to a security hole.

---

### Post by lexen on 2008-01-31
Wow, that is a really small program.  I think there is a chance because it won't boot any other program.

     What security hole is there?

---

### Post by maybeway36 on 2008-02-01
Does it work with Ubuntu's /bin/sh also? It's linked to /bin/dash which is not as featureful as bash but is faster.

---

### Post by buu700 on 2008-02-01
> **maybeway36 said:**
> Does it work with Ubuntu's /bin/sh also? It's linked to /bin/dash which is not as featureful as bash but is faster.

No, sorry. I would have used Dash/Sh, but the programs actually use a feature specific to BASH: the ability to easily set it to accept more than 9 arguments. However, for something like this, I'm sure the speed difference would be negligible anyways.

---

