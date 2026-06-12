---
title: "Quicklist editor"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Jacobonbuntu on 2012-04-19
Hi people,

a few months ago, as an experiment,  I started with a script to edit quicklists. I just finished the first GUI version, and plan to work it out (a lot) more.
If you care to try it out, please let me know, suggestions or (any) comment appreciated!
I should work on both Precise and Oneiric

[IMG]http://dl.dropbox.com/u/1155139/editor_window.png[/IMG]

You can download the QLE.zip file [here]("http://bazaar.launchpad.net/%7Evlijm/jonb.homelauncher/launchermaker/files") (updated almost daily)
installation: unzip it, open a terminal, cd to the directory of the setup.py file and run the command: "python setup.py"

---

### Post by mc4man on 2012-04-19
I'm gathering if users get a 'outdated desktop file' it's because the existing one is still using the X-Ayatana-Desktop-Shortcuts= instead of Desktop Actions (Actions=

firefox would be such an example, why it hasn't been changed yet don't know - it's updated more than enough times to have done so
(users can switch over if desired

? - I don't have any supported media player currently installed - would the available options include a new Exec=

---

### Post by Jacobonbuntu on 2012-04-19
> **mc4man said:**
> I'm gathering if users get a 'outdated desktop file' it's because the existing one is still using the X-Ayatana-Desktop-Shortcuts= instead of Desktop Actions (Actions=

firefox would be such an example, why it hasn't been changed yet don't know - it's updated more than enough times to have done so
(users can switch over if desired

? - I don't have any supported media player currently installed - would the available options include a new Exec=


The "carte blanche" option* is* an "Exec=" option (since now) , I don't see why Firefox and Thunderbird still have "Actions=" desktop files, but I will combine the "new" and "old" style editor in one version soon, just to make sure...

edit:
Ah, I read you post again...
at this point the install script reads the version from the default nautilus desktop file (if it has "Actions=" or not) and installs the corresponding editor_engine.py.

---

### Post by mc4man on 2012-04-19
I believe 12.04 will allow both (X-Ayatana-Desktop-Shortcuts= & Actions=), so there is some leeway for apps to rewrite their .desktops by 12.10

Still doesn't excuse FF & TB (unless ubuntu isn't in a possition to alter the source easily, though  can't see why not

(was wondering what "carte blanche" meant

---

### Post by Jacobonbuntu on 2012-04-19
> **mc4man said:**
> I believe 12.04 will allow both (X-Ayatana-Desktop-Shortcuts= & Actions=), so there is some leeway for apps to rewrite their .desktops by 12.10

Still doesn't excuse FF & TB (unless ubuntu isn't in a possition to alter the source easily, though  can't see why not

(was wondering what "carte blanche" meant

.......and the "Test" button is to check if the "Exec=" command is doing what you expected it to do....

---

### Post by Dngrsone on 2012-04-20
Jacobonbuntu, since you are now our resident quicklist expert (contratulations!  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/rolleyes.gif[/IMG] ), do you think you can weigh in on our discussion in [this thread](http://ubuntuforums.org/showthread.php?p=11858903#post11858903)?

---

### Post by Jacobonbuntu on 2012-04-21
Thanks for the invitation!
see you there..

edit: interesting thread! needs some experimenting...

---

### Post by Jacobonbuntu on 2012-04-21
> **mc4man said:**
> I'm gathering if users get a 'outdated desktop file' it's because the existing one is still using the X-Ayatana-Desktop-Shortcuts= instead of Desktop Actions (Actions=

firefox would be such an example, why it hasn't been changed yet don't know - it's updated more than enough times to have done so
(users can switch over if desired

? - I don't have any supported media player currently installed - would the available options include a new Exec=


...just fixed the "outdated desktopfile" issue...

---

### Post by Jacobonbuntu on 2012-04-23
> **Jacobonbuntu said:**
> Hi people,

a few months ago, as an experiment,  I started with a script to edit quicklists. I just finished the first GUI version, and plan to work it out (a lot) more.
If you care to try it out, please let me know, suggestions or (any) comment appreciated!
I should work on both Precise and Oneiric (still have to do some work on including "old style" desktop files in Precise)

[IMG]http://dl.dropbox.com/u/1155139/editor_window.png[/IMG]

You can download the QLE.zip file [here]("http://bazaar.launchpad.net/%7Evlijm/jonb.homelauncher/launchermaker/files") (updated almost daily)
installation: unzip it, open a terminal, cd to the directory of the setup.py file and run the command: "python setup.py"



you can download it from launchpad[ here]("http://bazaar.launchpad.net/%7Evlijm/jonb.homelauncher/launchermaker/files") (updated almost daily...)
(oops, I linked to outdated files, this one is right, download the QLE.zip)[/QUOTE]


Hi people, I discovered a potential problem, simpel to solve: the editor  creates an initial backup of either the default .desktop file, or (if  it exists) of the local one. the editor copied it to *application-name*_initial.desktop.  however, multiple .desktop files to the same application can cause  mixing up of the icon that is shown in the launcher, so changes you make  in the editor have seemingly no effect. it is fixed in the latest version; now the editor names backup files to .txt

please do the following: open the ~/.local/share/applications folder and  remove any file with a name ending with "-initial.desktop". possibly you will have to lock the application to the launcher again.

---

