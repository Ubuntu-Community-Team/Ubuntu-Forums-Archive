---
title: "Can't connect to apache2"
date: 2019-03-02
forum: Server Platforms
---

### Post by steemswede on 2019-03-02
Attempting to connect to apache2 using my public ip-address (port 80), but every site I'm using tells me that none of my ports are open. Canyouseeme.org says my ports are closed even though I opened them in the router.

Router: Netis WF2411
Operative system: Ubuntu server 16.04

---

### Post by darkod on 2019-03-02
What exactly do you mean by "opened them"?

Depending on the router, there maybe be two different steps, or they can be combined in one step.

You will for sure need to forward port 80 to the private IP of the server in the router. In some cases that is enough because it opens port 80 in the router firewall at the same time.

In cases the firewall is not opened with the above, you will need to also open port 80 in the router firewall settings.

Did you test opening apache locally from the LAN? Does it work? You need to test that too to make sure it works on server level.

---

### Post by SeijiSensei on 2019-03-03
If you're on a residential connection, your ISP might block traffic to port 80 to enforce a "no servers" rule. Are you sure your provider permits running web servers?

---

