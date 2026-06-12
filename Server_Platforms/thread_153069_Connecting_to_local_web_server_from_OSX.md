---
title: "Connecting to local web server from OSX"
date: 2006-03-31
forum: Server Platforms
---

### Post by Tim Thumb on 2006-03-31
I've set up a small LAN with a Ubuntu box as a file server and local web server (Apache). I've used Samba for file sharing as the LAN includes WinXP machines and a Mac with OSX.

Everything works perfectly apart from being able to connect to the web server using the Mac. In the WinXP machines I connect to this intranet in a browser with the address: [http://name_of_my_ubuntu_box](http://name_of_my_ubuntu_box) 

But when I try it from the Mac it just gives something like "Can't connect to server" even though I have no problem connecting to my shares.

Any help would be appreciated as it's driving me nuts.

---

### Post by gmclachl on 2006-03-31
I wrote a quick bit of apple script to connect to our development servers. 

 Open up script editor in OS X and enter 

 tell application "Finder"
	mount volume "smb://workgroup;user: password@ip|domain/sharename"
end tell 

change the values to suit your needs for instance my file looks like

tell application "Finder"
	mount volume "smb://MSHOME;developer:*******@192.168.0.15/developer" 
end tell

Also I found apple to be a bit fussy about connecting with you don't specify a share name. 

 So if I was to go to  

 GO > Connect To Server 
 
 and then just enter smb://192.168.0.99  it would cough a hairball (although 
it works fine with other OS's) you need to 

  smb://192.168.0.99/sharename 

HTH
George

---

### Post by Tim Thumb on 2006-03-31
George, isn't this just a way to see smb shares though? I can do that fine already, it's see the intranet that's the problem - will it fix that?

Thanks.

---

### Post by gmclachl on 2006-03-31
[QUOTE=Tim Thumb]George, isn't this just a way to see smb shares though? I can do that fine already, it's see the intranet that's the problem - will it fix that?

Thanks.[/QUOTE]
 Doh, makes mental note to read posts more carefully. I thought it was a problem with your samba shares 

Can't you try telnetting from the mac to port 80 of the target server. See what sort of response you get.

George

---

### Post by Tim Thumb on 2006-03-31
When I try:

$ telnet name_of_my_ubuntu_box 80

I get:

name_of_my_ubuntu_box: No address associated with nodename

So I tried the IP:

$ telnet 192.168.0.100 80   

and got:

Trying 192.168.0.100...
telnet: connect to address 192.168.0.100: Operation timed out
telnet: Unable to connect to remote host

If I do this to a WinXP machine running Apache from the Mac I can offer either the computer name or the IP address and each connects fine.

---

### Post by Tim Thumb on 2006-03-31
I must also note that from the Win machines I can only connect to the Ubuntu web server using [http://name_of_my_ubuntu_box](http://name_of_my_ubuntu_box) and not [http://192.168.0.100](http://192.168.0.100)

---

### Post by gmclachl on 2006-03-31
Hmmm, that's really weird. At work all our desktops run OS X and our development/version control servers run ubuntu.(I also have a powerbook at home) and I have never had this problem connecting to the servers at work or home through OS X. 

 ALTHOUGH 
 I do remember OSX coughing a hairball one day and not connecting to one of the development servers when I used an IP address. However when I used [http://kirk](http://kirk) (<- all our servers are named after Star Trek characters how sad is that ) it worked fine. 

Of course I had added the servers to the hosts file in OSX.

George

---

