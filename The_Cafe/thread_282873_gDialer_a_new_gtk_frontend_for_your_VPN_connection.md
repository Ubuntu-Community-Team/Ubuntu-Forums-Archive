---
title: "gDialer: a new gtk frontend for your VPN connection"
date: 2006-10-23
forum: The Cafe
---

### Post by mithras86 on 2006-10-23
Because the lack of graphical frontends for a VPN connection, I decided to learn python, and write my own one. I have given it a very original name: vpnDialer-gtk. The release I have now works quite well, but is lacking a lot of features and needs profiles configured in a non-safe way. 

First, a screenshot:
[IMG]http://sourceforge.net/dbimage.php?id=95682[/IMG]
**What can vpnDialer:**[LIST]
[*]creating a VPN connection with a given profile in the /etc/vpnc directory
[*]disconnecting this connection
[*]for security reasons, only one connection can be made at one time[/LIST]The only missing thing is that I don't know how to give the terminal your given password. *The password needs to be listen in the profile configuration file!!!*

**What are features vpnDialer will have:**[LIST]
[*]connecting with a given password
[*]creating and editing configuration files
[*]create a "quick-connection": no need to create a profile first, you can create a vpn connection immediately.[/LIST]
**Things to do**[LIST]
[*]design: I'm a complete noob with inkscape, so a logo design could take some time (now using a temporary one: Gaim's phone)
[*]Save the preferences (now only the profile directory) in a XML format[/LIST]
**Known bugs:**[LIST]
[*]A configuration profile should have a "Xauth password" entry, because when vpnDialer should provide the password, there is no connection created. See also [this thread]("http://ubuntuforums.org/showpost.php?p=1670297&postcount=16"). If anyone knows how to solve this, I'd really appreciate any hints![/LIST]
The project page of vpnDialer has been set up, and you can find it [here]("http://sourceforge.net/projects/vpndialer-gtk"). Please say what you think about it, and which features or changes you'd like to see.

---

### Post by kripkenstein on 2006-10-23
Looks good so far. Nice start.

"gDialer" isn't very clear about what the app is - dialing can refer to lots of things, not just vpns. VPN should be in there somehow - gVPNdialer, or something like that (hopefully better).

---

### Post by mithras86 on 2006-10-24
I've set a testversion online. You can download it [here]("http://juriansluiman.nl/vpndialer.tar.gz"). I hope I can solve the password thing quickly. When that's done, I'll release it as version 0.1.

---

### Post by gbutler69 on 2006-10-27
I downloaded it and tried. I'm not sure where you're going with this. The only option is to configure the password and connect/disconnect. Nothing for configuring the various VPNC options. Are you intending this?

I also think that "Dialer" is entirely inappropriate. This has nothing to do with dialing. You need connected over some network (DSL, Broadband, Dial-Up) *before* connecting to VPN. I think a better name would be something along the lines of "gVPNConf" or "gVPNManager". Better yet, get this functionality integrated into "NetworkManager".

Just an opinion.

---

### Post by mithras86 on 2006-10-27
> **gbutler69 said:**
> I downloaded it and tried. I'm not sure where you're going with this. The only option is to configure the password and connect/disconnect. Nothing for configuring the various VPNC options. Are you intending this?Yes, I am. But I'm completely new to Python, so it's not going really fast. I have now a working program, and I'm busy with the preferences. 
I want a complete program to configure vpn connections, so creating new profiles (= configuring various VPNC options) is a feature that certainly will be added.

If I get what you mean, you'd like to see a connection window to connect directly, without the need to specify a config profile. My intention was to design a gui to connect/disconnect with vpnc, and creating/editing profiles (like the ones now in /etc/vpnc).
I hadn't realized a "fast-connect" option would be very handy. It'll be a good feature for a next release ;)
> I also think that "Dialer" is entirely inappropriate. This has nothing to do with dialing. You need connected over some network (DSL, Broadband, Dial-Up) *before* connecting to VPN. I think a better name would be something along the lines of "gVPNConf" or "gVPNManager". Ok. I named it vpnDialer-gtk (renamed it after Kripken's suggestion), because of the already existing project [gvpn-dialer]("http://sourceforge.net/projects/gvpn-dialer/"). That project is dead, but if people are already using that program, vpnDialer-gtk doesn't look completely different. I don't speak or write English fluently, so the I'm not quite sure about the meaning of 'Dialer', but I thought vpnDialer indicates pretty well the function. In my English->Dutch dictionary, the definition is also (in the telecommunication) to create a connection.

vpnManger is also an idea, but I'm open for suggestions to rename it.
> Better yet, get this functionality integrated into "NetworkManager".I think that won't happen soon. NetworkManager is written in C or something and not in Pyhton, but it's also mainly to set up wireless connections (or actually, connect to APs). I don't use NetworkManager, because I have wired internet. In a screenshot of NetworkManager is saw a submenu called 'VPN Connection', but didn't found it when I installed nm...
And this program isn't for configuring your internet or network, just to create a vpn connection. It has atm nothing to do with the NetworkManger.

If nm has the option to connect/disconnect vpn connections, I'll use that. But it seems to me that nm doesn't have that built-in option right now.

---

### Post by DoctorMO on 2006-10-27
You'll want a vpn status on the gnome status panel (use gconf) and if you want python help give me a bell I offer free python training to open source developers.

The other thing is that I hear there is a VPN configuration tool which has just become available in Edgy Eft. I thought this topic was going to discuss that new tool but I don't have Edgy yet so I'm not sure. can someone clear this point up?

There is always room for stand along tools as they always seem to offer those extra options that gnome misses.

---

### Post by mithras86 on 2006-10-27
> **DoctorMO said:**
> You'll want a vpn status on the gnome status panel (use gconf) and if you want python help give me a bell I offer free python training to open source developers.Ok, thanks for the help! But what do you mean with the first part: "a vpn status on the gnome status panel"?
And if you don't mind, do you know how to solve [this problem]("http://ubuntuforums.org/showpost.php?p=1670297&postcount=16"). It's really stupid, because it's a vital part of the project :P

> The other thing is that I hear there is a VPN configuration tool which has just become available in Edgy Eft. I thought this topic was going to discuss that new tool but I don't have Edgy yet so I'm not sure. can someone clear this point up?If that's true, I haven't found it yet, and then I'll use that app ;) But sounds interesting, I'll search for it this weekend!

> There is always room for stand along tools as they always seem to offer those extra options that gnome misses.Mje, I don't like 100 projects targeting the same goal. If there is already a project running (which is not "my" vpnDialer), I'll talk to the project owners what I thought to develop. Then I could go on my next project (a gtk2+ interface for mp3gain, that's something i thought it's also non-existing)

About the development: it's going pretty well, and [here]("http://juriansluiman.nl/vpndialer.tar.gz") you can download the latest tarball. I put it in /usr/lib/vpndialer, but if you prefer another location, you should change the APP_PATH variable in common.py (you  can use a normal text editor like gedit to do it).

/edit: is see there is something wrong with the ownership. Maybe it happened during the archiving. All files should be owned by root, but that is not the most important thing. If you want to run the script, you should do that as a super user, because you need to access the /etc/vpnc/ directory

---

### Post by mithras86 on 2006-10-30
Ok, another bump. The first beta release is out! You can download it from the [sourceforge.net project page]("http://sourceforge.net/project/showfiles.php?group_id=180973") if you want.

About the existing vpnc support in Edgy: i heard several people about NetworkManager with support for vpnc connections. Is that true? I haven't found the option yet. but if nm can provide these connections, I'm stopping with this small project ;)

---

