---
title: "Unable to use Windows partitions in Ubuntu"
date: 2009-09-11
forum: Virtualisation
---

### Post by onlytanmoy on 2009-09-11
Dear All,

I am using VMWare Workstation 6.5.3 in my Windows 7. I have set up Ubuntu Linux as a virtual machine & added the partitions (NTFS) from my existing physical disk via Add disc in VM settings window. Problem is
though they are visible in Ubuntu but when i try to open them i get the below authentication window..

[img]http://i26.tinypic.com/2ugl2m0.jpg[/img]

"troy007" is my user id in ubuntu.

in spite of typing the correct password, i get the below error message

[img]http://i32.tinypic.com/dvriht.jpg[/img]

Nothing happens on clicking "Retry" or "Continue" & if i click "Abort", the ubuntu session gets disconnected.

Wats wrong?? Plz help :confused:
Thanks in advance,
Troy.

---

### Post by fjgaude on 2009-09-11
Open a terminal and do this:

```
sudo smbpasswd -a <yourID>
```

From there answer the prompts with your password.

That might be your problem, but maybe not. Doing this will do no harm in any event.

---

### Post by onlytanmoy on 2009-09-18
onlytanmoy is on a distinguished road


Join Date: Jul 2009
Windows 7
27 posts
 
	
  onlytanmoy is online now Add to onlytanmoy's Reputation   Report Post  

Default
problem solved...u need to have vmware tools properly installed in your linux guest to use shared folders...in vmware settings there is a provision to add a folder as shared thru a wizard, pretty easy..once u r done with these...the shared folder will show up under /mnt/hgfs :)

thanks again for ur help though mate...this thread is solved now.

---

