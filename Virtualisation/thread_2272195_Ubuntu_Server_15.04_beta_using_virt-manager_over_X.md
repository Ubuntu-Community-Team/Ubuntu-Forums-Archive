---
title: "Ubuntu Server 15.04 beta using virt-manager over X11"
date: 2015-04-04
forum: Virtualisation
---

### Post by mnix on 2015-04-04
Hello All,

I have a (probably) not so smart question.  I've just downloaded the Ubuntu Server 15.04 beta and was pleased to find that it includes qemu 2.2.0 since I've been trying to setup a vfio VM (using: [http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)) and am hitting the driver stop (code 43 issue, for which the kvm=off flag is apparently required--and not supported until qemu 2.1 and newer).  What is not so cool however is that on 14.04.2 I was able to use X11 forwarding to forward the virt-manager gui over to my windows machine (but had to build qemu, since 14.04.2 has version 2.0.0).  It appears that this no longer works out of the box, or that I'm doing something wrong now.  I was hoping someone could help me determine if this a bug (and what information to collect and how to report exactly) or if I just messed up.

I started out by installing Ubuntu Server 15.04 beta in EFI mode with ssh-server and virtual machine host selected.  I then ran ```
sudo apt-get update && sudo apt-get dist-upgrade
``` to make sure my packages were the latest.

I'm currently using the following line to get all my virtualization tools:

```
sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder virt-manager qemu-system uml-utilities
```

The first time I did this, this was one of my later steps, after stubbing the devices and all, so I thought maybe I did that wrong.  I installed again from scratch with the same options and just did the steps outlined here (no stubbing or modifying modules/initramfs or grub).

It's when I try to run virt-manager that everything seems not so well.  I get the following:
```
** (virt-manager:19721): WARNING **: Could not open X display
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused


(virt-manager:19721): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)                                                                                 ' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_settings_get_style_cascade: assertion 'GTK_IS_SETTINGS (s                                                                                 ettings)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_style_provider_private_lookup: assertion 'GTK_IS_STYLE_PR                                                                                 OVIDER_PRIVATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_lookup_resolve: assertion 'GTK_IS_STYLE_PROVIDER_PRIV                                                                                 ATE (provider)' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_css_rgba_value_get_rgba: assertion 'rgba->class == &GTK_C                                                                                 SS_VALUE_RGBA' failed


(virt-manager:19721): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)                                                                                 ' failed
/usr/lib/python2.7/dist-packages/gi/overrides/__init__.py:175: Warning: invalid (NULL) pointer instan                                                                                 ce
  return super_init_func(self, **new_kwargs)
/usr/lib/python2.7/dist-packages/gi/overrides/__init__.py:175: Warning: g_signal_connect_object: asse                                                                                 rtion 'G_TYPE_CHECK_INSTANCE (instance)' failed
  return super_init_func(self, **new_kwargs)


(virt-manager:19721): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion 'GDK_IS_SCREEN (screen)                                                                                 ' failed


(virt-manager:19721): Gtk-CRITICAL **: _gtk_settings_get_style_cascade: assertion 'GTK_IS_SETTINGS (settings)' failed



```

I did some googling and found that sometimes the display is not setup so I should try to run "echo $DISPLAY" and make sure I get a value (I do):

localhost:10.0

I also tried adding it as 127.0.0.1:10.0 (or something similar) that I found also by googling.

All still to no effect.

Hoping someone can help me figure out what I've got here and how to resolve it.

Thanks in advance!

---

### Post by mnix on 2015-04-30
Seem to be (mostly) working in the release version

Still get one error, but it launches:

```
** (virt-manager:1413): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-BK97K6nqgA: Connection refused

```

---

### Post by TheFu on 2015-05-03
virt-manager can be run from any Linux machine with graphics that has ssh access to the host KVM/QEMU/Xen/VirtualBox/LXC system. The host system does not need any GUI libraries, but you can run virt-manager on the host, if you load the GUI desktop tools there.  I don't.  **ssh -X** should setup the correct DISPLAY environment ...er ... always.  I've never seen it failed, provided X11-Forwarding is allowed on the X-client (the remove machine) in the sshd_config file.

So there is only 1 real trick to getting virt-manager working with a normal userid from a remote desktop.  On both the VM-host and on the machine running virt-manager, the userids involved (non-root) must be in the **libvirtd** group. Connecting as root brings other issues that I prefer to avoid. Then we can run virt-manager, use a remote ssh connection to manage the VM-host and all VMs inside it (there are certain limitations for LXC things still).  

Double clicking on any previously created VM will try to open a console to that machine using VNC thru an ssh tunnel. The performance is often poor, so I prefer to use normal ssh to manage servers and only use the console when other network methods are broke. If I need a remote desktop, x2go is the tool. Using plain ssh is best.

Hopefully, this doesn't confuse anymore.  My VM-host machines often do not have a GPU installed (why waste a slot AND $20?), so I'd prefer to use a desktop with a high-end $40 GPU instead. I'm serious, but realized this could be a joke to some. ;)

---

