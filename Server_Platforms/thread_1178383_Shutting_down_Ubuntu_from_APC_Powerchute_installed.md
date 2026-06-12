---
title: "Shutting down Ubuntu from APC Powerchute installed on a Windows server"
date: 2009-06-04
forum: Server Platforms
---

### Post by NSharp on 2009-06-04
I have been tinkering with this for a couple of days now and have finally realized why it was not working.

My shutdown command on the windows machine is ..

c:\progra~1\putty\plink.exe ups@server -i c:\progra~1\putty\key.ppk ./poweroff.sh

If this was run from a normal command prompt it would shut the box down fine. However when tested from powerchute it failed.

The reason being is the powerchute services are running at the system level and so the host key is not cached for the system user.

To overcome this simply add echo y | at the front of the command which accepts the key for you and shuts the server down nicely.

Once you have tested the command once and accepted the key into the registry for the system user you can then remove the echo y 

Hope this saves some others a bit of time

Nick

---

