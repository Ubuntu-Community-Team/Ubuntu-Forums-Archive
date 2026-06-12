---
title: "X2Go Desktop Sharing w/Client on 11.04"
date: 2011-11-27
forum: Tutorials
---

### Post by DapperMe17 on 2011-11-27
_Here's a tutorial to get X2Go Server w/Desktop Sharing using SSH Key Authorization on Ubuntu._

It is written with the assumption that there is no current SSH, or key pair present. Also assumed that the standard SSH port 22 is used, and all firewalls are set to allow the standard SSH port.

X2Go is a great little remote desktop solution; simple setup and secure! 

Here we go....

**1.** Visit Launchpad to get the PPA.......[https://launchpad.net/~x2go/+archive/ppa]("https://launchpad.net/~x2go/+archive/ppa")

**2.** On both the server PC & client PC, open Terminal and add the repository....
 
```
sudo add-apt-repository ppa:x2go/ppa
```

**3.** On the server PC, open Synaptic and install the following...

[HTML]x2goserver
x2godesktopsharing[/HTML]

*Install all of the recommended dependancies as well (Included will be SSH if it hasn't been previously installed).

**4.** On the client PC, open Synaptic and install the following...

[HTML]x2goclient[/HTML]

*Install all of the recommended dependacies here too. (Included will be SSH if it hasn't been previously installed).

**5.** On the client PC, open Terminal to generate the SSH key pair (you'll hit enter a few times to generate as default)...

```
ssh-keygen
```

**6.** On the client PC, navigate to your home folder and open the "hidden" folder .ssh. You will see your key pair there (id_rsa and id_rsa.pub). 

You will now have to copy your client public key "id_rsa.pub" to the server PC. This can be done at your discresion, such as by sftp. 

On the server PC, you will open the folder where you saved the client's public key. Open the key with any text editor (Gedit, Mousepad, etc...) and copy the information in that file. 

On the server PC, now open the home folder and look for the hidden folder .ssh. Open that folder and you will will see a file called "authorized_keys". Open that file and paste the client PC's public key into it. Once pasted, save the file and close. 

You've successfully exported your client PC's SSH RSA public key, into the server PC's SSH file. 

**7.** On the client PC, open X2Go Client and we'll set it up to use SSH Key Authorization by default.

Once open, click on the "New Session" icon and give it a name.

*Host:* Enter the IP of the server PC 
*Login:* The user name of the server PC
*Port:* 22
*Use RDA/DSA key for ssh connection:* /home/*****/.ssh/id_rsa (where ***** is the user name on the client PC)

*Session type:* Connect to remote desktop

Now, chose the connection tab, and chose your connection type from the slider.

X2Go Client is now ready for use. 

**8.** On the server PC, be sure you add [HTML]/usr/bin/x2godesktopsharing [/HTML]to the automatic startup applications in your system settings menu. 

[COLOR="Red"]UPDATE: At the moment, Step 8 appears to be unnecessary. In fact, you should not even have to start "x2godesktopsharing" from the application menu on the server side, as it works perfectly without the need to manually start it.    [/COLOR]

**9.** You're ready to connect.

Using the X2Go Client, click on your newly added session name, which will begin the connection. 

You will receive an initial pop-up box that asks you to accept the SSH fingerprint. Accept. (This key will be automatically placed in the client PC's .ssh folder, inside the "known_hosts" file)

**10.** You should now see an option to connect to the server session. Highlight the session name, and you will be offered two choices to connect to the server desktop (View Only or Full Control). Choose your preference to be connected to the "shadowed" session of the server PC via secure SSH tunnel, using your new RSA Key pair. (id_rsa used on the client side & id_rsa.pub on the server side)

That's it...enjoy X2Go!


:popcorn:

---

