---
title: "Using Eucalyptus"
date: 2009-04-30
forum: Virtualisation
---

### Post by harsha b on 2009-04-30
Hi,I was facing the issue that when I run the command 'ec2-describe-availability-zones' I get the error:

"Server: Binding 'ec2_amazonaws_com_doc_2009_03_01' not found for class edu.ucsb.eucalyptus.msgs.RunInstancesType"

I have followed the instructions given in "https://help.ubuntu.com/community/Eucalyptus". I have run wget for both "http://s3.amazonaws.com/ec2-downloads/ec2-api-tools-1.3-30349.zip" and "http://s3.amazonaws.com/ec2-downloads/ec2-api-tools-1.3-30349.zip" and  then run unzip for both. But I continue to get the same error. 

I am able to start eucalyptus-cloud normally. But when I start eucalyptus-nc I get the message "apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName". 
Is this the cause of the "Server:Binding" error?

I am running Xen3.x and I able to create VM's using virt-manager. But xenbr0 is not configured and I am unable to do resolve this  at the moment.

---

