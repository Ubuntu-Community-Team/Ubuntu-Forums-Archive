---
title: "Heartbeat - Pacemaker - Apache issues"
date: 2014-02-28
forum: Server Platforms
---

### Post by Jonay on 2014-02-28
[COLOR=#000000][FONT=verdana]Hi all,[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I have 2 nodes with heartbeat and pacemaker installed. Everything seems that works fine but I have a little problem and two doubts[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]First of all, this my crm configuration:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]node $id="1a806807-0ba5-4f82-9e68-552b80c18031" node01 \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]attributes standby="off"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]node $id="e50dc4cd-fd15-4819-8dda-fd144ab2546d" node02[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]primitive apacheha lsb:apache2 \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]op monitor interval="15s" timeout="20s"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]primitive haip1 ocf:heartbeat:IPaddr2 \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]params ip="192.168.1.90" cidr_netmask="32" nic="eth0" \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]op monitor interval="30s"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]location cli-prefer-haip1 haip1 \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]rule $id="cli-prefer-rule-haip1" inf: #uname eq node01[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]colocation apacheha-haip1 inf: haip1 apacheha[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]order ip-apache inf: haip1 apacheha[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]property $id="cib-bootstrap-options" \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]dc-version="1.1.7-ee0730e13d124c3d58f00016c3376a1de5323cff" \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]cluster-infrastructure="Heartbeat" \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]stonith-enabled="false" \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]expected-quorum-votes="1" \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]no-quorum-policy="ignore" \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]start-failure-is-fatal="false"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]rsc_defaults $id="rsc-options" \[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]resource-stickiness="100"[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]When I type: "crm node standby node01" everything works as expected, apache service promoted to node02 and the web service keep running. Then, when node01 is active again, the apache resource goes to node01 again. Everything perfect.... BUT[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]My problem: I just want to know if I type "/etc/init.d/apache2 stop, the pacemaker resource apache move to node02 but I cant check this cause there are something that restart the service apache2 almost instantly. Cause if node01 does not crash completely, but only apache2 service stop unexpectedly, can pacemaker be configure to migrate the resource to node02?[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Doubts:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]1) Why pacemaker is restarting apache2 service automatically and what can I do to stop apache2 service forever until I start it again?[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]2) I have a script that I just want to execute only in the active node, how can I know wich node is the master and how can I put that on a script?[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Thanks a lot in advance.[/FONT][/COLOR]

---

