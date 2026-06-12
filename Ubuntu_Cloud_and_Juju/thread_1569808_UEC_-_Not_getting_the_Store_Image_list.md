---
title: "UEC - Not getting the Store Image list"
date: 2010-09-07
forum: Ubuntu Cloud and Juju
---

### Post by deviprasad_k on 2010-09-07
I had installed Ubuntu enterprise cloud (ver UEC 10.04.1) and it is up and running. I had used 2 machine configuration wherein the Node Controller is installed on one server and the rest of the components (Cloud, Cluster, Storage, Walrus) are installed on another server.
 
The problem that i face is that there is no image shown in the store. Also, when i try searching for one, it displays a message "Error 6: Couldn't resolve host 'imagestore.canonical.com'".
 
Is it trying to connect to imagestore.canonical.com?
 
I don't have internet connection on this server and if it tries to connect to the imagestore.canonical.com, then is there an alternative to get the list of stores by some offline means and is there a way to get / install images ?

Thanks in advance.
Deviprasad K

---

### Post by Rusty au Lait on 2010-09-09
> **deviprasad_k said:**
> 
 
Is it trying to connect to imagestore.canonical.com?
 
I don't have internet connection on this server and if it tries to connect to the imagestore.canonical.com, then is there an alternative to get the list of stores by some offline means and is there a way to get / install images ?

Deviprasad K

I can not answer your question at this time. All kinds of incidents can be created but getting those from the store without admin? I do not know.

Here's one place [https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC) Get the eucalyptus manual there.

Follow smoser's links in a previous thread for an excellent example of incident creating.

---

### Post by baboli on 2010-09-09
> **deviprasad_k said:**
> I had installed Ubuntu enterprise cloud (ver UEC 10.04.1) and it is up and running. I had used 2 machine configuration wherein the Node Controller is installed on one server and the rest of the components (Cloud, Cluster, Storage, Walrus) are installed on another server.
 
The problem that i face is that there is no image shown in the store. Also, when i try searching for one, it displays a message "Error 6: Couldn't resolve host 'imagestore.canonical.com'".
 
Is it trying to connect to imagestore.canonical.com?
 
I don't have internet connection on this server and if it tries to connect to the imagestore.canonical.com, then is there an alternative to get the list of stores by some offline means and is there a way to get / install images ?

Thanks in advance.
Deviprasad K
You can download some already made  packages from : [http://open.eucalyptus.com/wiki/EucalyptusUserImageCreatorGuide_v1.5](http://open.eucalyptus.com/wiki/EucalyptusUserImageCreatorGuide_v1.5) and follow the installation procedure to get them in your cloud. 
I noticed that in the environment with firewalls blocking every port (high ports) the image list and store do not show anything. I tried from home network, everything is fine.
Vahid.

---

### Post by deviprasad_k on 2010-09-21
I had managed to install images.
 
Now, the Node Controller is running on a Virtual Machine running on VMWare ESX server. So, I am not able to enable VT in the bios. Hence I am not able to provision any instance of the new image.
 
I think the Node Controller machine should have VT enabled processor and should not be on a Virtual Machine. Is that right? Any comments.

---

### Post by Ohm's Lawyer on 2010-09-26
> **deviprasad_k said:**
> I had installed Ubuntu enterprise cloud (ver UEC 10.04.1) and it is up and running. I had used 2 machine configuration wherein the Node Controller is installed on one server and the rest of the components (Cloud, Cluster, Storage, Walrus) are installed on another server.
 
The problem that i face is that there is no image shown in the store. Also, when i try searching for one, it displays a message "Error 6: Couldn't resolve host 'imagestore.canonical.com'".
 
Is it trying to connect to imagestore.canonical.com?
 
I don't have internet connection on this server and if it tries to connect to the imagestore.canonical.com, then is there an alternative to get the list of stores by some offline means and is there a way to get / install images ?

Thanks in advance.
Deviprasad K

Hi There,
I have the same problem, and nearest I could tell is that imagestore.canonical.com is hard coded into the interface somewhere and perhaps some minor restructuring has happened over at canonical. Regardless, you can download images directly from both Ubuntu's site and Eucalyptus' site. You can also bundle your own images (there is a great tutorial if you Web Search for "Eucalyptus Beginners Guide").

Hope that helps a little.

---

### Post by Ohm's Lawyer on 2010-09-26
> **deviprasad_k said:**
> I had managed to install images.
 
Now, the Node Controller is running on a Virtual Machine running on VMWare ESX server. So, I am not able to enable VT in the bios. Hence I am not able to provision any instance of the new image.
 
I think the Node Controller machine should have VT enabled processor and should not be on a Virtual Machine. Is that right? Any comments.

Hmm....never tried running a node via VM, but the node controller goes on the same machine all of your instances will be running on. It seems to me that it might be a little taxing to run VMs on a VM if it is even possible to cascade like that.

To the best of my knowledge, you are correct in your assumption. The Node Controller (and by extension the Node itself) should probably be a physical machine and have a VT enabled processor.

---

