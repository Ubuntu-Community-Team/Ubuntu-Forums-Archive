---
title: "Ubuntu Server Team - June 1st, 2010 -  Meeting Minutes"
date: 2010-06-02
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-06-02
[IMG]http://fridge.ubuntu.com/files/Server.jpg[/IMG]


**[Server Team 20100601 meeting minutes]("http://ubuntuserver.wordpress.com/2010/06/02/server-team-20100601-meeting-minutes/")**

Here are the minutes of the meeting. They can also be found online with the irc logs [here]("https://wiki.ubuntu.com/MeetingLogs/Server/20100601").

 


**Action points from the last meeting**

 

[LIST]
[*]sommer to try to move server doc spec to Ubuntu specs: DONE 
[*]ttx to document (or delegate documentation of ) package stack names: DONE 
[/LIST]
**Alpha1 milestone**

 

The Alpha1 milestone will be released Thursday. Please participate to [Server ISO testing]("http://iso.qa.ubuntu.com/qatracker/build/ubuntuserver/all") to get as much coverage as we can. Current known issues include an oversized CD, due to bug [587893]("https://bugs.launchpad.net/bugs/587893"). smoser will publish cloud images soon. Between now and Alpha1 we are in soft freeze and should not upload major changes that could impact negatively the milestone.  

ACTION: all to run ISO testing coverage on alpha1  

ACTION: smoser to ensure cloud images make it to the alpha1 iso tracker  


**Alpha2 subcycle status**

 

The Canonical team tracks progress on their specs [here]("http://people.canonical.com/~pitti/workitems/maverick/canonical-server-maverick-alpha-2.html"). Please remember to keep your work items and Status: line updated in the blueprints, at least once per week before Monday EOB. See the [WorkItemsHowto]("https://wiki.ubuntu.com/WorkItemsHowto") for more info. ttx will reset the trends line tomorrow to something more useful to track progress.  

[server-maverick-cloud-kernel-upgrades]("https://blueprints.launchpad.net/ubuntu/+spec/server-maverick-cloud-kernel-upgrades") needs some attention since there is some work separation between smoser and jjohansen, and a more detailed work items plan is desired.  

On the community side, Mail & cluster stack look in great shape. jib asked to seperate items out for before & after feature freeze to help track things. The doc spec is also in good shape.  

ACTION: smoser to coordinate with jjohansen and ttx to provide a more detailed work item overview for server-maverick-cloud-kernel-upgrades  


**Weekly Updates & Questions for the QA Team**

 

hggdh verified bug [565101]("https://bugs.launchpad.net/bugs/565101"), which should go to -updates as soon as possible. Additionally, he also did a quick test of bug [586134]("https://bugs.launchpad.net/bugs/586134"), and seems to work with 512 loop devices configured. There might be a delay in the Eucalyptus SRU due to a potential regression on bug [566793]("https://bugs.launchpad.net/bugs/566793").  


**Weekly Updates & Questions for the Kernel Team**

 

jjohansen is in vacation, so no progress yet on pv-ops. SpamapS mentioned that the proposed PTRACE changes would also affect negatively the ops population, and will chime in on the thread to make that concern known.  


**Weekly Updates & Questions for the Documentation Team**

 

Lucid serverguide PDF is available on h.u.c. For next week&#8217;s meeting, sommer will present new sections for which the doc team will need input from the server team.  

ACTION: sommer to present list of sections that need input from server team  


**Papercuts selection for Alpha2 subcycle**

 

We currently have [14 bugs nominated]("http://tinyurl.com/papercuts-nominations") for a desired total of 16 targets, so choosing between them should be easy. Last-minute nominations can still occur since ttx will proceed with formal selection tomorrow morning. You can also start assigning yourself to those you&#8217;re interested in.  


**Weekly SRU review**

 

SRU nominations were reviewed. The tracker for the new SRU process is under work, with an early view accessible [here]("http://people.canonical.com/~chucks/SRUTracker/").  


**Open Discussion**

 

[server-maverick-openldap-dit]("https://blueprints.launchpad.net/ubuntu/+spec/server-maverick-openldap-dit") was reviewed and approved. EtienneG brought up the question of which iSCSI target is being chosen for main/UEC: tgt is the answer, and ccheney will work on the MIR, and zul on the upstartification.  


**Agree on next meeting date and time**

 

Next meeting will be on Tuesday, June 8th at 18:00 UTC in #ubuntu-meeting.  

Originally posted to the [ ubuntu server blog]("http://ubuntuserver.wordpress.com/2010/06/02/server-team-20100601-meeting-minutes/") by Theirry Carrez on Wed Jun 2, 2010



[More...](http://fridge.ubuntu.com/node/2048)

---

