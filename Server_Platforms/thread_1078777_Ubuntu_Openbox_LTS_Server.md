---
title: "Ubuntu Openbox LTS Server"
date: 2009-02-23
forum: Server Platforms
---

### Post by Hozza on 2009-02-23
Hi i have a Ubuntu 8.04 LAMP server
 running XDM and Openbox GUI, 

can i set up a remote desktop connection to it so that i can access it form any computer (with a password)???

---

### Post by Hozza on 2009-02-24
:bump: anyone???

---

### Post by freerkkalsbeek on 2009-02-24
That's not so difficult, the question is: What kind of access do you need.
For console access:
sudo apt-get install openssh-server and then connect from any client using ssh user@hostname

For X application : ssh -X user@hostname

If you want full desktop access: install freenx-server on the server and the NoMachine client on the client

Client can be obtained at: [http://www.nomachine.com](http://www.nomachine.com)
For freenx-server use repo: deb [http://ppa.launchpad.net/freenx-team/ubuntu](http://ppa.launchpad.net/freenx-team/ubuntu) intrepid main

Freerk

---

### Post by Hozza on 2009-02-25
ah ok (i will use that), but i was looking for a GUI access, what then?

---

### Post by Hozza on 2009-02-28
:bump: anyone?

---

### Post by hrod beraht on 2009-02-28
> **Hozza said:**
> ah ok (i will use that), but i was looking for a GUI access, what then?

GUI access on a server? Off the top of my head, I honestly can't think of anything I do in maintaining my servers where a GUI would actually be helpful.

Maybe we're approaching this from the wrong direction. What exactly is it you want to do on your server? Or is your question more along the lines of "what does it take to administer a server?"

Bob

---

