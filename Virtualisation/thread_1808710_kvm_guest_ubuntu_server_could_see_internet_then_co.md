---
title: "kvm guest ubuntu server could see internet then couldn't?"
date: 2011-07-20
forum: Virtualisation
---

### Post by mpp-2011 on 2011-07-20
Having managed to create a first guest on an ubuntu server host, the guest being ubuntu server too, I could ping the local network fine but not the internet, then I added forwarding for the guest to the host using the iptables command.  Also I added the nameservers as on local network machines that could see the internet, and also edited the guest hosts file to identify the guest there, also updated the hostmane file.  iptables -L showed the guest forwading rule alright.

Rebooted the guest and the host.  Reentered the forwarding rules and this time used iptables-save and iptables-restore, iptables -L still shows the rules for guest forwarding alright.  From the guest I can still pint the local network machies but now cannot ping the internet.

Not sure why it worked for one session then it hasn't worked since.

Anyone seen this before please?

---

### Post by mpp-2011 on 2011-07-23
Since my post, I have found on a couple of test runs recently, that with the forwarding rues set using iptables as mentioned in the original post, if I wait for some time, then if I ping the guest from the host using the guest machine name to ping to, shortly after this, then the guest manages to ping out to the internet.

On the second occasion, this at first only worked when pinging google, then after more time I could also ping yahoo and the bbc.

Perhaps it takes time for some information to get stored on the host so that the forwarding works or else maybe it takes a ping from the host to the guest to bring the information needed to be set?

---

### Post by Dark_Ichigo on 2011-07-26
> **mpp-2011 said:**
> Having managed to create a first guest on an ubuntu server host, the guest being ubuntu server too, I could ping the local network fine but not the internet, then I added forwarding for the guest to the host using the iptables command.  Also I added the nameservers as on local network machines that could see the internet, and also edited the guest hosts file to identify the guest there, also updated the hostmane file.  iptables -L showed the guest forwading rule alright.

Rebooted the guest and the host.  Reentered the forwarding rules and this time used iptables-save and iptables-restore, iptables -L still shows the rules for guest forwarding alright.  From the guest I can still pint the local network machies but now cannot ping the internet.

Not sure why it worked for one session then it hasn't worked since.

Anyone seen this before please?


I have a Question aside of yours if I may, How did you manage to create a guest host on your Ubuntu Server Host?
Im currently trying to do some LDAP integration but I need a Server and a Guest(Client) host first.....If its not too much trouble and sorry for interfering with your question...could you please tell me how?

Thanks!

---

