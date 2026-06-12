---
title: "Getting &quot;panic: runtime error: index out of range [0] with length 0&quot;"
date: 2021-11-25
forum: Ubuntu, Linux and OS Chat
---

### Post by bjornand on 2021-11-25
[COLOR=#000000]Hi, I run Homebridge in Docker on a Synology and I would really like to get the [([https://github.com/frli4797/homebridge-sector#readme)](https://github.com/frli4797/homebridge-sector#readme))] plugin to work. This relies on a server, [([https://gitlab.com/deftware/sectoralarmapi)](https://gitlab.com/deftware/sectoralarmapi))], but as far as I can tell, it is not possible to run it in the Synology environment, so I have installed Ubuntu Linux on an always-on Mac. [/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I have downloaded the Linux binary and run the "preparatory" steps to make it executable and run without sudo as explained here, [([https://gitlab.com/deftware/sectoralarmapi)](https://gitlab.com/deftware/sectoralarmapi))], and that seemingly works, at least there are no error messages. [/COLOR]

[COLOR=#000000]When running the command to set the environmental variables and executing the binary, however, I get an error message:

[/COLOR]
[COLOR=#000000]larmlinux --http "0.0.0.0" panic: runtime error: index out of range [0] with length 0

[/COLOR]
[COLOR=#000000]goroutine 1 [running]: 
main.createSession(0x30) /go/src/gitlab.com/deftware/sectoralarmapi/client.go:72 +0x397 
main.Login(0x8) /go/src/gitlab.com/deftware/sectoralarmapi/client.go:88 +0x37 
main.Setup() /go/src/gitlab.com/deftware/sectoralarmapi/main.go:33 +0x22 
main.main() /go/src/gitlab.com/deftware/sectoralarmapi/main.go:25 +0xb8

[/COLOR]
[COLOR=#000000]I have tried replacing the 0.0.0.0 ip address with that of the Mac and the Ubuntu install, but with the same result, so really stuck here!

Any ideas how to solve this?[/COLOR]

---

