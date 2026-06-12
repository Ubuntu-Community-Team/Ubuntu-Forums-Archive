---
title: "Unable to install IEs4linux"
date: 2010-10-29
forum: Wine
---

### Post by periaganesh on 2010-10-29
Hi all,
   I'm new to ubuntu and even linux. I installed wine using Synaptic Manager. The following are the programs that got installed.
1.wine 1.2-1ubuntu1~lucidppa1 Microsoft Windows Compatibility Layer (dummy package)
2.wine1.2-gecko 1.0.0-0ubuntu4 Microsoft Windows Compatibility Layer (Web Browser)
3.winetricks 0.0+20100917-0ubuntu1~lucidppa1 Microsoft Windows Compatibility Layer (winetricks)
4.wine1.2 1.2-1ubuntu1~lucidppa1 Microsoft Windows Compatibility Layer (Binary Emulator and Library)
5.wisotool 0.0+20100731 Microsoft Windows Compatibility Layer (wisotool)

I also installed cabextract.

After that I download IEs4Linux from [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation) and when I try to install it the following is the error that is displayed.

[COLOR=Red]IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

/home/ganeshp/programfiles/softwares/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:268: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
ui/pygtk/python-gtk.sh: line 6: 11696 Segmentation fault      python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py[/COLOR]


Can someone please help me install IEs4Linux as I need it to test my site on IE.

---

### Post by Humanity to others on 2010-10-29
You can try playonlinux to install ie6 or ie7
for the installation you can use ubuntu software centre or synaptic package manager.
or try
[http://www.playonlinux.com/script_files/PlayOnLinux/3.8.5/PlayOnLinux_3.8.5.deb](http://www.playonlinux.com/script_files/PlayOnLinux/3.8.5/PlayOnLinux_3.8.5.deb)

---

### Post by Leighman on 2010-10-30
Or run
winetricks ie6
or 
winetricks ie7

---

