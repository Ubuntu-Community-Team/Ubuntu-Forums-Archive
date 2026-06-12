---
title: "instance show running but not appear in NC"
date: 2013-01-23
forum: Ubuntu Cloud and Juju
---

### Post by asraa on 2013-01-23
I can run instance , ping it and ssh it as admin from the CLC machine  ( i implemented the private cloud in two machines one contain clc cc sc walrus controller and the other is node controller )

i bring another machine installed Linux desktop in it  and obtain credential from cloud url   and installed euca2tool in it to act as client  make request to my cloud  
i create a keypair and run instance with it   euca-run-instances -k mykey emi-E01E107B 
the instance show pending then running but i cant ping or ssh  the ping show destination unreachable  in NC when i used command  ¨virsh list "  it doesn't list my running instance 
despite that my instance status show running   

i checked there is no problem in LAN  network connection  i can ping NC and CLC from client mechine 

please help

---

### Post by asraa on 2013-01-23
now it get worse  when i try to run instance in the client machine  it keep pending then terminate  never run  but i still can run instance from CLC controller 
  please help:(

---

