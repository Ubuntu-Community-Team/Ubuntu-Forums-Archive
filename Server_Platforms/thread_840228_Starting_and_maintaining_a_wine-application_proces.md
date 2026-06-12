---
title: "Starting and maintaining a wine-application process on a vps"
date: 2008-06-25
forum: Server Platforms
---

### Post by chevron on 2008-06-25
Hello guys,

I need some help:
I have installed a program(MetaTrader4) via wine on my ubuntu-vps. I can start it without any problems using ssh and x11-forwarding. 
Yet my problem is, I want to keep it running when I log off. Everytime I execute it, the window appears on my desktop and when i shut it down, the process is killed.
I have searched through the internet but have not found a _working_ solution.
I have already tried:
-nohup
-dtach
-disown
-screen
None of them worked.

I know, it could work with a gui and vnc, but i only have a small vps and would prefer not to waste my HDDspace installing a desktop environment.

I hope you can help me.

---

### Post by DA_uf on 2008-07-02
I'm intrigued by your approach to MetaTrader[4].

What is ubuntu-vps? I found this [http://vpslink.com/ubuntu-vps/](http://vpslink.com/ubuntu-vps/)
Do you have a plan with them?  If so, which one?

Is "ubuntu-vps" a server installation of Ubuntu running in a virtual environment but acting like a dedicated server from your point of view?

I'm looking for a stable way to run MetaTrader and I have zero intentions to run it on MS Windows with real money.

If ubuntu-vps is non-GUI, I don't see how you can maintain MetaTrader4 (which has a GUI -- no?).

I have been testing Ubuntu 8.04 LTS Server Edition - Supported to 2013 locally, to see if I will be able to run a custom application using the MetaTrader 3 API with a dedicated server from maybe serverpronto.com.

I've used ssh and ran GUI's which would display on my local machine, but again, I don't think it is technically possible to maintain such a GUI after the local and remote machines are disconnected, except like you mentioned with VNC.

If you are using a host, do they allow installing a desktop environment?  Which one?  (I understand you don't like that option, but it may be an option for me).  Would you explain how that would work with a GUI and VNC?  What about SECURITY?

I'll start a new thread, but the reason I'm on the forum today is because I'm trying to have Wine run 2 Message-Only windows, since I do not need a GUI:
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

---

