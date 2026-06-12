---
title: "azureus on a server"
date: 2006-01-08
forum: Server Platforms
---

### Post by Simpel on 2006-01-08
Hi there

I run my ubuntu as a server, in other words, it stands in my closet and...just works I use it for storing files and such!

Today I came up with the idea that I want to install azuerus on it at use azureus through a terminal...I followed this guide to install it:

[http://ubuntuforums.org/showthread.p...ght=bittorrent](http://ubuntuforums.org/showthread.p...ght=bittorrent)

and that worked fine. But, and here is the newbie question. How do I use it through a terminal, where can I find a list of different commands, and in what catalogue can I find Azureus now??

/simpel

---

### Post by doogy2004 on 2006-10-04
the best thing to do is install one of the web plugings for azureus and access it useing your web browser

---

### Post by frolle on 2006-11-10
Oh, how do i do that? Been trying for so long.

---

### Post by bobpaul on 2006-11-10
[size=4]**Azureus Console Mode**[/size]
Well, here's a guide that talks about [installing with console support]("http://www.azureuswiki.com/index.php/ConsoleUI").

Basically you put the two jars in your azureus folder and then run: ```
java -jar Azureus2-XXX.jar --ui=console
``` On my system, I run: ```
java -jar /opt/azureus/Azureus2.jar --ui=console
```

When you start azurues in console mode you can type "help" for a list of commands. You can type "set" to see available options. Change options by doing "set option.name choice". Eg, to change the connection port to 12345, I might do "set Core_iTCPListenPort 12345" 
**Note** Console commands are case sensitive!

 I'm not sure how to install plugins from console mode, though, so...

[SIZE="4"]**Installing plugins with the wizard**[/SIZE]
1) If you have X installed on your server just launch azureus normally. If you *don't* have X installed or there's no monitor, try doing remote X forwarding. You need ssh-server installed to do this. From another machine do: ```
bobpaul@bobpaul:~$ ssh -XC user@ip-address
``` where user is a user on your server and ip-address is the ip-address of your server. Ex "ssh -XC mythtv@192.168.10.11" is how I connect to my mythtv box. Now you can run azureus and the interface will appear on your local computer!```
 mythtv@mythtv:~$ azurues
```

2) From the **Plugins** menu choose **Installation Wizard...**. Follow the wizard and install a webui. I prefer "HTMLWebUI". Other options are "Swing Web Interface" and "XML over HTTP". You can also try telnet access.

3) Connect! For HtmlWebUI, the port is 6886, so fireup a webbrowers and connect to [http://ip-address:6886](http://ip-address:6886) where ip-address is the ip of your server.



If step 1 doesn't work for you, try these alternate instructions:
[SIZE="4"]**Installing plugins manually**[/SIZE]
1) Find the plugin you want from [the list](http://azureus.sourceforge.net/plugin_list.php). You'll want one of the plugins from 2 above.

2) Click the frog to download the jar file. Save it to ~/.azureus/plugins/PLUGINNAME (you have a create a folder for each plugin in the plugins folder).

3) Start azureus from the console

4) Open a browser and connect [http://ip-addrss:port](http://ip-addrss:port) where ip-address is the addrss of your server and port is the port for the plugin your using. Htmlwebui is 6886, not sure about the others.

---

