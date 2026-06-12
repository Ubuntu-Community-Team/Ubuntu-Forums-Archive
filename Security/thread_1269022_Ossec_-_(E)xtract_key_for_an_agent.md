---
title: "Ossec - (E)xtract key for an agent"
date: 2009-09-17
forum: Security
---

### Post by JohnWesleyMethodist on 2009-09-17
I have been fumbling around for hours now trying to get Ossec installed and working for the first time.

 I have been to this screen before:

```

(server)# /var/ossec/bin/manage_agents

****************************************
* OSSEC HIDS v2.2 Agent manager.       *
* The following options are available: *
****************************************
   (A)dd an agent (A).
   (E)xtract key for an agent (E).
   (L)ist already added agents (L).
   (R)emove an agent (R).
   (Q)uit.
Choose your actions: A,E,R or Q:

```

 and while at that screen I chose option E and was given a long password. Several reboots later and other modifictions completed, I am finally able to get this screen:

```

(agent)# /var/ossec/bin/manage_agents

****************************************
* OSSEC HIDS v2.2 Agent manager.       *
* The following options are available: *
****************************************
   (I)mport key for the server (I).
   (Q)uit.
   Choose your actions: I or Q: 

```

 The problem I have now is that I didn't paste the password I got when I chose option E above and now I can't figure out how to extract the password again. Can anyone help me with a command that will allow me to extract the password?

 Using Ubuntu Jaunty.

 Thanks!

---

### Post by The Cog on 2009-09-18
The option to extract the key is done on the server - the server makes the keys which you give to the clients as a proof of identity. The import is done on the clients. So I don't see what all the rebooting is about. Am I misunderstanding whwat you're trying to do?

When I do it, I tend to use VNC or SSH to remote one from the other, and then I can copy/paste the key, which is easier than transferring it by USB stick.

---

### Post by JohnWesleyMethodist on 2009-10-06
Thanks for your reply. The reason for all the reboots is because I can't seem to get this page of instructions to work properly:

 [http://www.ossec.net/main/manual/manual-manage_agents-tool/](http://www.ossec.net/main/manual/manual-manage_agents-tool/)

 I got fed up with trying before and I uninstalled everything. Now today I am following this tutorial and I only get the first screen:

```

****************************************
* OSSEC HIDS v0.8 Agent manager.       *
* The following options are available: *
****************************************
   (A)dd an agent (A).
   (E)xtract key for an agent (E).
   (L)ist already added agents (L).
   (R)emove an agent (R).
   (Q)uit.
Choose your actions: A,E,R or Q: a

```

 I can't now get to the next screen:

```

****************************************
* OSSEC HIDS v0.8 Agent manager.       *
* The following options are available: *
****************************************
   (I)mport key for the server (I).
   (Q)uit.
   Choose your actions: I or Q: i

```

 The full instructions I am attempting to follow are below:

```

 1. First, you need to add the agent to the server. You just need to run the “manage_agents” command, provide the IP Address of the agent and choose a name for it (or username).

(server)# /var/ossec/bin/manage_agents

****************************************
* OSSEC HIDS v0.8 Agent manager.       *
* The following options are available: *
****************************************
   (A)dd an agent (A).
   (E)xtract key for an agent (E).
   (L)ist already added agents (L).
   (R)emove an agent (R).
   (Q)uit.
Choose your actions: A,E,R or Q: a

- Adding a new agent (use ‘q’ to return to main menu).
  Please provide the following:
    * A name for the new agent: linux1
    * The IP Address for the new agent: 192.168.2.32

    * An ID for the new agent[001]:
Agent information:
    ID:001
    Name:linux1
    IP Address:192.168.2.32

Confirm adding it?(y/n): y
Added.

2. After your agent is added, you need to extract the authentication key from your server. In the “manage_agents”, just choose the “E” option and provide the ID of the agent. The key to be used by the agent will be printed. Just copy and paste it in the agent side.

(server)# /var/ossec/bin/manage_agents

****************************************
* OSSEC HIDS v0.8 Agent manager.       *
* The following options are available: *
****************************************
   (A)dd an agent (A).
   (E)xtract key for an agent (E).
   (L)ist already added agents (L).
   (R)emove an agent (R).
   (Q)uit.
Choose your actions: A,E,R or Q: e

Available agents:
    ID: 001, Name: linux1, IP: 192.168.2.32
    ID: 002, Name: obsd1, IP: 192.168.2.10
Provide the ID of the agent you want to extract the key: 001

Agent key information for ‘001&#8242; is:
CDAxIGxpbnX4MSAxOTIuMTY4LjAuMzIgOWM5MENlYzNXXXYYYZZZZZ==

** Press ENTER to continue

3. After you key is generated, you need to copy it and paste it on the agent side. You need to run the same “manage_agents” command in the agent (but it will have some different options).

(agent)# /var/ossec/bin/manage_agents

****************************************
* OSSEC HIDS v0.8 Agent manager.       *
* The following options are available: *
****************************************
   (I)mport key for the server (I).
   (Q)uit.
   Choose your actions: I or Q: i

* Provide the Key generated from the server.
* The best approach is to cut and paste it.
*** OBS: Do not include spaces or new lines.

Paste it here: CDAxIGxpbnX4MSAxOTIuMTY4LjAuMzIgOWM5MENlYzNXXXYYYZZZZZ==

Agent information:
    ID:001
    Name:linux1
    IP Address:192.168.2.32

Confirm adding it?(y/n): y

Added.
** Press ENTER to continue.

****************************************
* OSSEC HIDS v0.8 Agent manager.       *
* The following options are available: *
****************************************
    (I)mport key for the server (I).
    (Q)uit.
Choose your actions: I or Q: q

manage_agents: Exiting ..

```

---

### Post by The Cog on 2009-10-07
Steps 1 and 2 are performed on the OSSEC server.
Step 3 is performed on the client machine.

Are you trying to install the agent on the server, or on a different machine?

If you're installing client and agent on separate machines, then you should not be getting the menu shown in step 2 on the client machine - you have installed the server by mistake. I think you need to uninstall and reinstall, specifying a client install this time.

If you're just trying to get OSSEC running on a single machine, I don't think you need to install the agent as well as the server. I think a server install also does the scanning of the local machine.

---

