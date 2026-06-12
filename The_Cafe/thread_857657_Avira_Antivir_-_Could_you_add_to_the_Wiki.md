---
title: "Avira Antivir - Could you add to the Wiki?"
date: 2008-07-12
forum: The Cafe
---

### Post by fiddledeedee on 2008-07-12
Hi!

You have a great page already in the wiki
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Could you add please Avira Antivir (I know the windows version which is very good in speed, detection and look & feel.)? Compiling the kernel module dakuzo is kinda hard and instructions on google are outdated for hardy.

I would be glad if someone could add some documentation.

---

### Post by aysiu on 2008-07-12
A Wiki is editable by anyone. Why ask others to add it when you can add it yourself?

---

### Post by fiddledeedee on 2008-07-12
> **aysiu said:**
> A Wiki is editable by anyone. Why ask others to add it when you can add it yourself?

Because I lack the technical knowledge how to install AntiVir.

So I am asking here if someone could add it.

---

### Post by robertyou on 2008-10-03
Go to [http://www.free-av.com/en/download/download_servers.php]("http://www.free-av.com/en/download/download_servers.php") and download both tar.gz package and license file on Desktop.

Open up a terminal and type following commands:

1. **cd ~/Desktop**

2. **sudo tar -xvzf name_of_the_file.tar.gz **

//(extract the package to a folder)

3. **cd ./name_of_the_folder_you_just_extracted**

4. **sudo sh install **

//(start the installation)

5. //and just follow the installation guide carefully on terminal

6. //when asked to enter the path to the license file enter the path where you downloaded it (say desktop).. 

Enter:

**~/Desktop/hbedv.key**


7. //be sure to answer yes for GUI installation if you're not familiar with command-line


8. //After installation complete. To start Antivir GUI, type following in terminal..

**sudo antivir-gui**


P.S. you need to have sun Java to use gui

---

### Post by jrusso2 on 2008-10-03
I think antivir is pretty easy how about dazuko?

---

### Post by robertyou on 2008-10-14
> **jrusso2 said:**
> I think antivir is pretty easy how about dazuko?

Yeah..about that. After reading some more posts here, I'm convinced linux might just be safe enough to run without an antivirus software..

Decided to remove avira before I finish dealing with dazuko :lolflag:(actually to my knowledge you need to have dazuko installed and compiled before avira is installed..)

---

