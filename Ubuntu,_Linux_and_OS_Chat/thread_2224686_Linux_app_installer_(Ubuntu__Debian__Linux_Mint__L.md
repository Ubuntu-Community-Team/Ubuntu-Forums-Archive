---
title: "Linux app installer (Ubuntu / Debian / Linux Mint / LMDE)"
date: 2014-05-17
forum: Ubuntu, Linux and OS Chat
---

### Post by cesargon on 2014-05-17
[COLOR=#333333][FONT=Helvetica]Menu to install applications from default repositories, third-party ones or external sources on any **Ubuntu** 14.04, **Debian** 7, **Linux Mint** 17 or **LMDE** system (desktop or server). There are a lot of applications included in the default list, but this list can be modified by the user by just editing a single text file. Furthermore, users can add subscripts to extend main menu functionality, for example, add new repositories, setup applications, etc. In addition, exist one separate script for each application as an alternative way to do the installation proccess without the main menu.
[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]

[/FONT][/COLOR][IMG]https://raw.githubusercontent.com/cesar-rgon/linux-app-installer/gh-pages/images/screenshots/screenshot-zenity.jpg[/IMG]         [IMG]https://raw.githubusercontent.com/cesar-rgon/linux-app-installer/gh-pages/images/screenshots/screenshot-dialog.jpg[/IMG]

**Valid for**:   Ubuntu v14.04, Debian 7, Linux Mint 17 and LMDE (for all desktops or server). With some changes in config files, it can be 100% compatible with previous versions.
**Version**:     1.2
**Github project**: [https://github.com/cesar-rgon/linux-app-installer](https://github.com/cesar-rgon/linux-app-installer)

**DONE**
[LIST]
[*]Added compatibility with Ubuntu 14.04 (unity/gnome/kde/xfce/lxde/server)
[*]Added compatibility with Debian 7
[*]Added compatibility with Linux Mint 17 (cinnamon/mate)
[*]Added compatibility with LMDE (cinnamon/mate)
[/LIST]
[INDENT]
[/INDENT]
**TODO**
[LIST]
[*]Develop Github web page
[/LIST]
[INDENT]

[/INDENT]
**1. Features**
[LIST]
[*]&#8203;One main script that shows a menu of aplications wich can be selected for installation.
[*]Alternatively, there is one separate script for each application, so it can be installed by just executing the appropriate script.
[*]Install official repository applications.
[*]Add third-party repositories and install related applications when needed.
[*]Download, extract and install non-repository applications through custom subscripts that extend the main script functionality. It includes several subscripts by default.
[*]Set up applications after they are installed through custom subscripts.
[*]Customize your own application list to install and third party repositories to add by just editing some config files (no need to edit main script at all for this purpose).
[*]EULA support. Install applications automatically with no need of user interaction to accept legal terms of the application.
[*]The script runs with an interface adapted to the detected enviroment: Dialog for terminal. Zenity for desktop or terminal emulator.
[*]Installation log file that shows installation steps and errors if they have occurred.
[*]Multilingual support. Easy to add new translations. For the time being English and Spanish languages are included. The script detects system language and it use the appropiate translation.
[/LIST]


**2. Installing this project**

**2.1 Method 1. Clone this repository**

```
[COLOR=#333333][FONT=Helvetica][COLOR=teal]$ [/COLOR]sudo apt-get install git
[COLOR=teal]$ [/COLOR]git clone -b master https://github.com/cesar-rgon/linux-app-installer.git
[COLOR=teal]$ [/COLOR][COLOR=#0086B3]cd [/COLOR]linux-app-installer[/FONT][/COLOR]
```

**2.2 Method 2. Download and extract files**

```
[COLOR=#333333][FONT=Helvetica][COLOR=teal]$ [/COLOR]wget https://github.com/cesar-rgon/linux-app-installer/archive/master.tar.gz
[COLOR=teal]$ [/COLOR]tar -xvf master.tar.gz
[COLOR=teal]$ [/COLOR][COLOR=#0086B3]cd [/COLOR]linux-app-installer-master[/FONT][/COLOR]
```


**3. Executing a script**

**3.1 Main script**

[COLOR=#333333][FONT=Helvetica]It shows a menu of applications to be installed which are ordered by categories. The user navigates through categories and selects the applications to be installed. After that, installation process begins.
[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Helvetica][COLOR=teal]$ [/COLOR]bash installer.sh[/FONT][/COLOR]
```

**3.2 Application script**

[COLOR=#333333][FONT=Helvetica]There is one separate script for each application, so it can be installed just by running the appropriate script.
[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Helvetica][COLOR=teal]$ [/COLOR]bash ./scripts/applicationName.sh[/FONT][/COLOR]
```


**4. Execution's lifecycle**
[LIST]
[*]&#8203;The user must select the applications to install.
[*]The script would add third-party repositories of the selected third-party applications, when required.
[*]The script executes custom subscripts to prepare the installation of some applications.
[*]The script installs all the selected repository applications with EULA support if required.
[*]The script executes custom subscripts to install the selected non-repository applications.
[*]The script executes custom subscripts to setup selected applications.
[*]The script runs final operations to finish installation process and to clean temporal files.
[*]The script shows an installation log file which contains installation steps and errors if they have occurred.
[/LIST]
[COLOR=#333333][FONT=Helvetica]Main script runs all the previous steps, whereas individual application scripts skip step 1 and run the remaining.[/FONT][/COLOR]


**5. Extend functionality and customize applications to install**

[COLOR=#333333][FONT=Helvetica]To extend script functionality is required to add subscripts for custom purposes. To customize applications to install, it's necessary to edit some config files. These actions will be detailed in next chapters.

For more information, **visit [Github project]("https://github.com/cesar-rgon/linux-app-installer")**.[/FONT][/COLOR]

---

### Post by bapoumba on 2014-05-17
*Thread moved to **Ubuntu, Linux and OS Chat**.*
I've had a quick look, how does it play with upgrades when people install third party repos ?

---

### Post by cesargon on 2014-05-17
Hi bapoumba.
Do you mean if people had installed their own third-party repos?

I don't see any problem with that. The subscripts are totally customizable. You can customize subscripts to add your favorite repos or delete files if you don't want to add any third-party repos at all.

Regards

---

### Post by bapoumba on 2014-05-17
> **cesargon said:**
> Hi bapoumba.
Do you mean if people had installed their own third-party repos?

I don't see any problem with that. The subscripts are totally customizable. You can customize subscripts to add your favorite repos or delete files if you don't want to add any third-party repos at all.

Regards

Well, if I understand correctly from what I've seen (and I may be wrong), the scripts get to install apps from third party repos (maybe also ppas, I do not recall). Would a basic user be aware of that ? On releases upgrades, it is better to disable them as some do not play nice.

---

### Post by deadflowr on 2014-05-17
> 
[LIST]
[*]EULA support. Install applications automatically with no need of user interaction to accept legal terms of the application.
[/LIST]


Can you still read the EULAs? 
I find it important to know what I'm agreeing to.

---

### Post by cesargon on 2014-05-17
Hi.
Most of applications in the list are installed from official repositories, only a few ones need to add third-party repos and the other ones are installed from external sources (wget ..., tar ..., create application links).
If a user selects one or more third-party applications in the list, the script will automatically add necessary third-party repos and then install the selected applications. At this moment, there isn't warning message about this.

What do you suggest? Warning message? Add third-party repo, install application and, after that, disable third-party repo?

Thanks. Regards.

EDIT: Other solution would be... to quit all third-party-repos by default and to install this few applications from external sources (wget ..., dpkg ... etc)

---

### Post by cesargon on 2014-05-17
Hi deadflowr.
The only one package that uses EULA is "ttf-mscorefonts-installer" to install Microsoft's true type fonts. If you delete ./eula/ttf-mscorefonts-installer file, the window to accept terms of use will appear again.

Regards.

EDIT: I think it's interesting to be available this feature in the script, but if you think that it's not suitable being enabled by default, i can delete previous file.

---

### Post by bapoumba on 2014-05-17
Thanks.

re: third party repos and ppas.
Ubuntu 14.04 was released not long ago. You can browse out support forums and will see that even knowing they had third party repos or ppas, many users did not disable them and had issues. So installing a package this way with your app, I think users should get a message saying they need to disable them before next release upgrade and check after the upgrade if the repo has packages for their new release.
If things go wrong, you may end up being in the loop for the blamings ;)

And thanks deadflowr, I missed the auto-accept EULA for mscorefonts.
```
ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true
```
I think EULA are here to be explicitly accepted by users.

---

### Post by cesargon on 2014-05-17
Ok.
I'm going to make an update of the script soon to to take account of these things.

Thank you.

---

### Post by bapoumba on 2014-05-17
Thanks :)
Please post back here when you're done.

---

### Post by cesargon on 2014-05-18
Hi all.
The scripts have been updated to version 1.11.

I have made the next changes relating to EULA support and adding third-party repositories:


1. EULA support.
The files "eula/ttf-mscorefonts-installer" and "eula/wine" are still there, but the content has been commented, so it takes no effect.
# ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true

This means:
    Basic user: Must accept EULA terms whatever application selection done.
    Advanced user: He/she can uncomment previous file, add new applications to the list and create new EULA files (all under his/her knowledge).


2. Third-party repositories
Following subscripts have been deleted:
    third-party-repo/Chrome.sh
    third-party-repo/Faenza.sh
    third-party-repo/Google_earth.sh
    third-party-repo/ubuntu/Grub_customizer.sh
    third-party-repo/ubuntu/Skype.sh
    third-party-repo/ubuntu/jDownloader.sh
    
As replacement, following subscripts have been created:
    non-repository-apps/Chrome.sh
    non-repository-apps/Faenza.sh
    non-repository-apps/Google_earth.sh
    non-repository-apps/ubuntu/Grub_customizer.sh
    non-repository-apps/debian/Skype.sh
    non-repository-apps/ubuntu/Skype.sh
    non-repository-apps/jDownloader.sh

This means:
    Basic user: No warnings, no adding third-party repos at all whatever application selection done. The previous applications are installed from external sources throught wget,dpkg,etc.
    Advanced user: He/she can add third-party repos just creating the corresponding subscript in "third-party-repo" folder (all under his/her knowledge).

I hope you like this solution to cover needs of basic and advanced users.
Regards.

---

### Post by bapoumba on 2014-05-18
Thank you :)

---

### Post by cesargon on 2014-05-23
Hi all.
I have updated Linux app installer to v1.2.

Main feature of this release is adding support to Linux Mint 17 (cinnamon and mate, for the moment) and LMDE (cinnamon and mate).

Regards.

---

