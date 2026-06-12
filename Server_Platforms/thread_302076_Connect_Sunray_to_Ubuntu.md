---
title: "Connect Sunray to Ubuntu"
date: 2006-11-18
forum: Server Platforms
---

### Post by eldaria on 2006-11-18
I was looking at [https://help.ubuntu.com/community/UbuntuOnSunRay](https://help.ubuntu.com/community/UbuntuOnSunRay)
At work we use some 25 Stations with 3 Sunray's each to run 3 screens per station.
However this is done connecting to 2 Unix Servers.

I have started developing R.S.I and need some special tools, but there are no drivers for Unix, and therfore it will not work on the Unix desktop.

I have tested and found that the tools works on (K)ubuntu Edgy 6.10, so therefore I wanted to set up a machine to provide me with connectivity via the sunray stations.
But I do not need to set up a complete Server, since the Sun servers will still provide DHCP, firmware updates, etc.

I tried to follow [http://klomdark.servebeer.com:8081/MessageBase2/ReadMessage.aspx?MsgNum=1967](http://klomdark.servebeer.com:8081/MessageBase2/ReadMessage.aspx?MsgNum=1967)
Just to enable remote X, but got an error message from the Sunray when trying to connect telling me that the remote host is valid, but that it may not be running dtlogin (Or other X display manager)

Not sure if this is the Sunray or the Kubuntu machine, (My Private laptop used for testing)

But is it possible to install only the connector for sunray without installing all the server stuff such as DHCP, Apache etc?

---

