---
title: "Methods to store password for an encrypted filesystem"
date: 2010-11-27
forum: Security
---

### Post by SeijiSensei on 2010-11-27
I admit off the bat that I've never created an encrypted file system so these questions may seem ridiculous.

I've created encryption systems on servers, but nearly always I have stored the password somewhere on the machine itself.  The file is always 0600 to the relevant user, but a systematic analysis of my system could easily find the scripts that invoke decryption and discover the password.  

(The most blatant example of this is mounting SMB shares with the "-o credential_file" option where both the username and password are plain-text. In the cases where I've used this, the security of the share hasn't particularly mattered.)

Soon I might be faced with storing "patient health information" (PHI in the healthcare world) whose privacy is heavily regulated by the provisions of the US law called [HIPAA]("http://www.hhs.gov/ocr/privacy/").  I've been thinking about creating an encrypted partition to hold the PHI, but I need a highly fault-tolerant method for obtaining the key from a different machine than tha server itself.

At first, I thought about running a script using scp and shared keys to copy the key from the remote, use it to decrypt the partition, then erase it.  I'd like to be able to do this with a pipe; otherwise I'll write the key in a non-persistent location like /dev/shm.  

I need more than one machine to make this work to ensure I can obtain the key when needed (like at boot).  One solution is to place copies of the key on multiple servers and try each of them until I find it.  A more elegant solution would place the key in a DNS TXT record.  I suspect I could use LDAP for this as well, but OpenLDAP and I have never really been on speaking terms.  

So does this make sense?  I presume I can write a bash script to do all this at boot.  Most of what will be stored in this partition is the PostgreSQL database in /var/lib/pgsql and perhaps some other files.  

My understanding of encrypted file systems is that they are only encrypted when unmounted.  When mounted they must be as visible to the operating system as an unencrypted partition.  I suppose you could apply encryption to every single disk transaction, but that would require knowing the key all the time, and would seem to add a lot of overhead.

---

### Post by SebastianG63 on 2010-11-28
Could you explain the scenario of your database machine and it's clients a little more detailed?

It seems a little hard to understand what and where this password and database partion obscurification will take place and when I look at your HIPAA reference, the major problem in my eyes becomes to securly identify the real world person and his/her role when accessing a specific health information. So the problem is perhaps a lot more about identifiying the real world persons trying to access PHI-data and their granted roles, than about encrypting partitions?

About physically storing highly sensitive data, there is only one feasible way at this time, rent a server at a secure data centre to disallow any unathorized physical access to the physical machines. Do not allow to access the server and it's database from anywhere outside of the data center in any way, as well as to any of the backups produced. The physical server must be a trusted place, if not so, make it trusted by security personal!

Have a machine that will mediate for checking access rights and roles form the database and play as a mediator between the server and anyone else. This mediator is the only machine allowed to access the server/PHI-database and also responsible for initiating backups. The mediator stores no passphrases from or for the server, but uses encryption in a key challange response way, initiated by the PHI-server on a per access base. Do only allow PHI-data updates/retrival for one person at a single request based on the person identification and role, but no bulk data processing of any kind. Record all activities.

And now comes the biggest problem in all this, make sure, that a real world person requesting operations by mediator on the PHI-database is actually the correct person and has the correct role to do so! This needs elektronically readable ID-Cards and passwords that can be checked in an encrypted form against the encrpyted ID and passwords/roles stored in your PHI-server, or at least the mediator machine can forward this along with the data request and let the server check if the request was authorized.


I live in Europe and when it comes to highly sensitive data in the industry over here, data access is commonly not solved accross database connections, but as encrypted data/request containers(files) accross ftp from one machine to anyother (Bank/Telecommunication Sector). All database operations are exclusivly solved from the contents of the containers locally and the only operations from outside are ftp transfers via a mediator machine.
To prevent man-in-the-middle-attacks all servers and the mediator are highly time sychronized (NTP/GPS) and a encrypted data container has from it's encoding/encryption scheme only a small time window for becoming processed. A client has to ask the mediator for a timestamp for encoding/encryption of a request/data container. If the time window passes before transaction, the data container will be rejected.
There is no physical connectivitiy between the secure data center and outworld, apart from physical cables between the data center to the mediator-machine and from the mediator-machine to the outworld.
Any pysical data storage medium must be made unusable within the data center before the remains are allowed to leave the data center physically, and this may only be done by certified companies, who guaranty the remains will immediatly be destructed/reduced (mostly fired in thermal power stations over here), since law here does not allow such remains to be stored in any way (even not overnight!).

So to say in general, the idea about storing PHI-data is perhaps more about a trusted server environment, restricted physical server access and limited electronic access on a per person and role base, not about storing passwords for encrypted filesystems. If you need to think about where to store passwords for encrypted filesystems, your concept is a priori not secure, since it basically relies on obscurification!

---

