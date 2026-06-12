---
title: "Absolute Virtualization Beginner Question"
date: 2007-11-16
forum: Virtualisation
---

### Post by twoseids on 2007-11-16
Is there a way I can share files between my VM and Ubuntu? I used VMware before, but it seemed like VMware created an alternate dimension for all my files, and that if I wanted to share them with Ubuntu, I needed to save them on a thumb drive, flip over to Nautilus and then read them off the thumb drive.

Or am I missing something here? Can I easily read VM-created files on Ubuntu, and can I read Ubuntu-created files from my VM?

I'm thinking about using VirtualBox this time around - would the answer be the same for that one too?

Thanks!

---

### Post by veloce on 2007-11-16
Virtual network between vm and host works well using vmware server.

---

### Post by paul.matthijsse on 2007-11-16
Hello, I am using VirtualBox and it is no problem to share files between the host and the VM. You'll have to mount the shared folder on the host though from within the VM. That procedure is clearly explained in the help file of VirtualBox, under "Folder Sharing".

Edit. Forgot to say that you need to install the LinuxAdditions first, those come together with the VirtualBox package.

---

### Post by twoseids on 2007-11-21
Thanks guys!

---

### Post by dpj23 on 2007-11-21
I'm use vmware and can tell a couple of ways to share files between the host operating system and the guest... O.K., 1 thing to remember it can be looked as a strategy as well...  You can build a XP pro machine and make 12GB which is plenty of space for an operating system...  Provided the bulk of your information is saved on the host and not in the quest...  

A couple of ways that I have used in the past and currently use....

1. create a shared folder on the host...  and with a XP guest create a mapped drive to that folder... Then re-target the My Documents folder into that drive... 

2. create a shared folder and browse to it...

3. transferring files should be easier now that you can cut/paste, drag/drop right from one-another in vmware....  I have not tried any other virtual software other than VMware...  

Nonetheless, I have been using VMware no for 5 years and would really recommend their software...

---

### Post by aparigraha on 2008-01-29
this is what i did. and it is the only way i made it work without crashing the guest OS.

first create a shared folder in VMware. (Workstation, doesn't work in Server)

VM->Settings->Options->Shared Folders->Always Enabled->Add

Restart VM

And then in, if you are in XP:

   1. Open the Explorer.
   2. Type \\.host in the Address field.
   3. Press Enter.
   4. Right-click on the Shared Folders icon.
   5. Choose Create a Shortcut.
   6. Click Yes to the message Windows cannot create a shortcut here. Do you want the shortcut to be placed on the desktop instead?

now access your Share directly from the Desktop.

---

