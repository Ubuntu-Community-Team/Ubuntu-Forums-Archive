---
title: "arreter le bluetooth"
date: 2010-06-03
forum: Tunisia Team
---

### Post by micronet on 2010-06-03
Bonjour
avec Ubuntu 10.04 le bluetooth est activé à chaque démarrage. alors je suis obligé de l'eteindre manuellement, chose qui est tres genant.
Alors je veux savoir quel commande permet d'eteindre le bluetooth pour le lancer au démarrage? ou peut etre qu'il y a une autre methode plus simple??

merci d'avance

---

### Post by Neo31 on 2010-06-03
hi there,
I believe you can do that using a simple GUI tool you can find at *("System > Administration > services" menu in older systems, but it has been moved in new Ubuntu systems to) ***"System > Administration > Start up applications" menu** (*Applications au demarrage*). Then simply disable the Bluetooth service.
it is that simple ;)
:)

---

### Post by micronet on 2010-06-05
thanks for the reply. but this tip will stop the bluetooth-applet only. 
the bluetooth(hardware) is always on !!!
any other tip ???

---

### Post by Neo31 on 2010-06-05
please before going trough this try to verify if the bluetooth service is still running, you can use the command line :
[COLOR=DarkSlateGray]service | grep tooth[/COLOR]
or
[COLOR=DarkSlateGray]service[/COLOR]


if it is still running try to install a package called **bum**, you can try installing it using the Software manager (Logitech), synaptics or what ever or this command line : [COLOR=DarkSlateGray]sudo apt-get install bum[/COLOR]
then look for a graphical tool called Boot Up Manager in the menus or try typing it's name in terminal [COLOR=DarkSlateGray]bum[/COLOR] or something like that. disable bluetooth, reboot and verify again.


If this doesn't work, I belief you'll have to go to a lower level, command line. I used Fedora for a long time before Ubuntu where the command line to turn off services was : [U][COLOR=DarkSlateGray]chkconfig bluetooth off[/COLOR]
but this wont work for Ubuntu[/U], I searched the Internet for the alternative command and it was (use this on your own risk, I didn't verify any of these commands) :

[COLOR=DarkSlateGray]sudo update-rc.d bluetooth purge[/COLOR]

or using sysv-rc-conf ([COLOR=DarkSlateGray]sudo apt-get install sysv-rc-conf[/COLOR])
[COLOR=DarkSlateGray]sudo sysv-rc-conf bluetooth off[/COLOR]

or using sysvconfig ([COLOR=DarkSlateGray]sudo apt-get install sysvconfig[/COLOR])
[COLOR=DarkSlateGray]sudo sysvconfig bluetooth off[/COLOR]


Please write feedback of the solution that worked for you :)


ps : I am sorry that I can't try and see which is the best and right tip of these since I installed a server I am working on these days in place of my ubuntu and I cannot restore it for now nor have time to try it anywhere else. Use the commands on your own risk, based on [this document]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/%20RedHatEnterpriseLinuxAndFedora") it says it's the alternative to the command I used on Fedora, if so that is supposed to work a 100%.

---

