---
title: "upgraded to hardy vmserver broke"
date: 2008-12-23
forum: Virtualisation
---

### Post by emtjr928 on 2008-12-23
I upgraded easily from gutsy to hardy. Was expecting to have to fix my vmserver.
Ran sudo vmware-config.pl

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] 

If I run anyway it will abort.

Question: How can I fix this? gcc 4.2.3 doesn't appear in the repositories. I have searched and not found the easy answer. 
Thanks Ed

---

### Post by inobe on 2008-12-23
things to consider...


if you used backports and went back to 4.2.3. you could break something in hardy' it may lead to a list of missing dependencies.

or you could recompile the kernel and lose your setup.

i learned the hard way upgrading myself, never upgrade running virtual machines, even after reinstalling' i had problems.

---

### Post by HermanAB on 2008-12-23
Yup - Don't fix it if it ain't broke.  If you have VMs running, you quickly learn to leave the system alone...

---

### Post by emtjr928 on 2008-12-24
Well, I had upgraded from gutsy to Hardy with updatemanager. To fix my VM I uninstalled VMserver and then downloaded and reinstalled. Everything went fine and my win2K virtual machine was still there and now works fine.

---

### Post by inobe on 2008-12-24
> **emtjr928 said:**
> my win2K virtual machine was still there and now works fine.

wow' i wasn't so lucky, congrats man :)

---

