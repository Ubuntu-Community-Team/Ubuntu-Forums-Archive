---
title: "Interaction between two Clouds"
date: 2010-12-13
forum: Ubuntu Cloud and Juju
---

### Post by snehalmasne on 2010-12-13
I have setup the cloud1 with 1 - [CLC+CC] and 2 - [NC]  computers. I have another cloud2 with same configuration.


 Both of them working fine individually, in the same LAN. 
 

Now if I want to add the NC of cloud1 to CC of cloud2, [in case the  resources of cloud2 are exhausted] how can I make it possible ? I guess  this calls for the interoperability stuff...
 

Could you please explain what happens exactly when we ask for  instance, the direct interaction happens between the client and NC or it  goes through the CLC and CC ?
 

I am sorry if I'm doing mistake anywhere...  Thanks in advance  :)
 



Regards,
[www.TechProceed.com]("http://ubuntuforums.org/www.TechProceed.com")

---

### Post by kim0 on 2010-12-13
I dont believe that is possible .. And I don't believe it should be supported either :) .. What you're probably looking for, is 1 cloud with a HA CLC+Walrus I think

---

### Post by snehalmasne on 2010-12-21
> **kim0 said:**
> I dont believe that is possible .. And I don't believe it should be supported either :) .. What you're probably looking for, is 1 cloud with a HA CLC+Walrus I think


                              Thank you so much Kim for replying.. :)
 what I want to say is, say there are multiple cloud providers. A user  is subscribed to any one of them, AAA for IaaS. As the requirements are  dynamic, all the resources of AAA may get exhausted and that provider  cant ask the client to go for BBB.
 So if it is possible to have some co-ordination between this two  providers to share resources mutually, making client fully unaware of  whats going on in the background....? 
 

Please reply.. 





 Regards,
[www.TechProceed.com]("http://www.techproceed.com/")

---

### Post by kim0 on 2010-12-27
Well you may achieve something of similar effect writing high level scripts to orchestrate operations across two clouds. However nothing of that sort exists out of the box today. Moreover, if a single entity controls AAA and BBB, then it definitely makes more sense to merge both clouds. If however AAA is private and BBB is public for example, then writing your own management scripts may help as mentioned

---

### Post by snehalmasne on 2011-01-20
hey kim, thanks again for replying.. :)

Could you elaborate the 'writing high level scripts to orchestrate operations across two clouds', I mean is it possible using some of the programming languages or architectures like REST or SOAP ?

---

### Post by raymdt on 2011-01-20
Hi,
yes you can use REST or SOAP to do that but i recommend to use ready-made Libraries like  typica, JCloud  (Java)  or the Excellent BOTO library (Python).
The best languages to achieve it are  Bash and Python, because euca2ools is java and BOTO is the most complete lib for AWS and Eucalyptus.

---

### Post by raymdt on 2011-01-20
Hi,
yes you can use REST or SOAP to do that but i recommend to use  ready-made Libraries like  typica, JCloud  (Java)  or the Excellent BOTO  library (Python).
The best languages to achieve it are  Bash and Python, because euca2ools  is java and BOTO is the most complete lib for AWS and Eucalyptus.

---

### Post by raymdt on 2011-01-20
Hi,
yes you can use REST or SOAP to do that but i recommend to use  ready-made Libraries like  typica, JCloud  (Java)  or the Excellent BOTO  library (Python).
The best languages to achieve it are  Bash and Python, because euca2ools  is java and BOTO is the most complete lib for AWS and Eucalyptus.

---

