---
title: "Problems With Samba PDC"
date: 2006-05-10
forum: Server Platforms
---

### Post by linuxmad on 2006-05-10
I have created a samba PDC following the "famous" tutorial that is at [http://howtoforge.com/samba_setup_ubuntu_5.10](http://howtoforge.com/samba_setup_ubuntu_5.10). I got everthing working.. but now that I am adding machines and users I am facing a strange problem. In order to create the users I used a script to add them in bulk. The user logs in and it uses the netlogon to apply a proxy.reg that automatically configures internet explorer to use a network proxy. The thing is that when the user first logs in everything seems to work, but after that(in several machines) I am getting a windows pop up notepad error (see attachement) that is driving me nuts.. I also attached smb.conf and proxy.reg. 
Please try to help.
Thanks
José

---

### Post by lonetree on 2006-05-22
Hi Linuxmad,

wonder if you have slved your problem with the text editor thing. I do face this problem when I was doing my test server.

I did a search on the internet it says it has got something to do with Desktop.ini (in windows), I went to the *drive%*/Document and Setting/Startup/ and another 2 folders, which I can't remember off hand, I deleted the Desktop.ini file and log off and log in again , and the problem is solved. I can't tell what the implication will be if I delete the files, but I guess it does no harm to the windows.

If you have solved the problem other than this method, please do share with me.

Thanks

Regards,

---

### Post by linuxmad on 2006-05-22
lonetree... glad .. I am not the only one...:D 
Well I did a little googling .. and appears this is not a Samba Issue ...it is.. A MS issue....take a look... [http://support.microsoft.com/default.aspx?scid=kb;en-us;330132](http://support.microsoft.com/default.aspx?scid=kb;en-us;330132)
...and their solution is only useful if you have one user or two... because if you have 100 or more their solution is not pratical... so... I found out that lots of people were having our problem and their solution is to put the red line below in your profiles share. However I found this to work only in new users, to the existent you will have to delete the entry as explained by MS. At least for me... this worked... Hope I helped..
Regards ...


[profiles]
path = /var/lib/samba/profiles
browseable = no
writeable = yes
default case = lower
preserve case = no
short preserve case = no
case sensitive = no
[COLOR="Red"]hide files = /desktop.ini/ntuser.ini/NTUSER.*/[/COLOR]
write list = @smbusers @root
create mode = 0600
directory mode = 0700

---

### Post by lonetree on 2006-05-23
Thanks linuxmad,

I think this is definitely going to help. The method that I suggested in my previous post will be time consuming.

By the way, do you have problem loggin in to Windows without the presence of samba DC? My mobile user can't login to his Windows XP when he uses hist notebook at home. Windows will prompt him with an error message saying that "The system cannot log him on as the domain is not present"

Let me know if you have this problem.

Thanks

Regards,

---

### Post by linuxmad on 2006-05-23
Considering your problem .. I really couln't replicate it with a laptop, however .. what I did was to disconnect the ethernet cable from the Samba PDC, and tried to log in from a windows machine on the network. This way the client machine wont find any domain server, and it logs in using a cached profile (local profile) still it warns you that it was not possible to log in to the server. What I mean, is that if your users used their profile on that client machine at least once, they will be able to log in offline..still they are warned about not using their roaming profile...
Please let me know your progresses...:)

---

### Post by lonetree on 2006-05-23
Thanks again for sharing,after the user has been added in the notebook, he uses it in the office, doing his daily work. Then when he went home and turns on his notebook, that is when the problem arise. I thought everything was fine until when he reached home and found out this problem. This is quite unusual as back then when I was using Windows DC, users were able to log in to their profile even without the presence of the DC. 

Anyway, thanks again, guess I will go back and create a test server myself and see if this problem arises.

Regards,

---

### Post by Iowan on 2006-05-23
XP has an alternate configuration option.  I use it to connect to non-networked machines on the plant floor - when the laptop connects to the network, it gets it's IP via DHCP.

---

### Post by lonetree on 2006-05-24
[QUOTE=linuxmad]Considering your problem .. I really couln't replicate it with a laptop, however .. what I did was to disconnect the ethernet cable from the Samba PDC, and tried to log in from a windows machine on the network. This way the client machine wont find any domain server, and it logs in using a cached profile (local profile) still it warns you that it was not possible to log in to the server. What I mean, is that if your users used their profile on that client machine at least once, they will be able to log in offline..still they are warned about not using their roaming profile...
Please let me know your progresses...:)[/QUOTE]


Hi Linuxmad,
just a few more questions for you. Did you managed to get your roaming profile working? Can the user change their password with Ctrl+Alt+Del? It seems that windows will hang with the hour glass spinning and spinning.

Thanks

Regards,

---

### Post by linuxmad on 2006-05-24
Hi lonetree,
About profiles....YES I was able to to put them to work. The only thing that does not work is the walpaper changing. I change the walpaper in one machine... log out...login in another machine with the same user and the walpaper doesn't change...even though if I click properties i look at the walpaper and it is the one I was using on the other machine. If after this I apply changes it updates the wallpaper...beats me....](*,) 
Now about ... changing passwords... You can do two things...
1) The line that says: 
```
unix password sync = yes
```
put:
```
unix password sync = no
```
and this way you will be able to alter your paswords in windows, ..however I think this way unix and samba passwords wont get syncronized... but samba passwords are updated and the client machine does not hang.
2) You can update your /etc/samba/smb.conf 
```
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n
```
to:
```
passwd chat = *password* %n\n *password* %n\n *success*
```
and it shoud work....:) 
Ok guess it is all...
Please let me know. about your progresses;)

---

### Post by Haulfron on 2006-05-26
[QUOTE=lonetree]Thanks again for sharing,after the user has been added in the notebook, he uses it in the office, doing his daily work. Then when he went home and turns on his notebook, that is when the problem arise. I thought everything was fine until when he reached home and found out this problem. This is quite unusual as back then when I was using Windows DC, users were able to log in to their profile even without the presence of the DC. 

Anyway, thanks again, guess I will go back and create a test server myself and see if this problem arises.

Regards,[/QUOTE]
I used to have same problem when our company had different NT domains at different sites. A visiting windows laptop defaults to looking for own domain and refuses to login when local DC does'nt respond. Manually choosing workgroup login was workround until AD.

---

### Post by mattoid on 2006-07-15
Linuxmad; Hi
how famous is this build guide? I just followed it, and when the machine first boots I cannot seem to get any admin rights, even when I log into root. I have a post regarding this at

[http://www.ubuntuforums.org/showthread.php?t=215819&highlight=pdc](http://www.ubuntuforums.org/showthread.php?t=215819&highlight=pdc)

if you or any of your correspondents here could take a look and maybe suggest something, I would be a very happy bunny indeed!

cheers

---

