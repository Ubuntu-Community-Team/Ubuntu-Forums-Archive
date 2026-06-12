---
title: "How to create a SSL CA?"
date: 2009-12-23
forum: The Cafe
---

### Post by Jekshadow on 2009-12-23
I am creating an internal CA, and I want to do it "right", as in giving each certificate the right permissions, etc. I looked up some online guides on how to do it, and all of them produced CA certificates that also acted as server certificates and email certificates, and the server certificates that were signed were server, client and email certificates. Does anybody know of a good guide that sets up the CA so that it is only a CA, and the server certificates so they they are only server certificates? Or just a good intro to using OpenSSL would work too.

---

### Post by seo4ssl on 2010-02-01
I would like to create a SSL certificate with multiple subject alternative names with my internal PKI so that I can use ISA Server 2006 to secure OWA and ActiveSync. Importing the root CA to different machines and PDAs is pretty simple, but my ActiveSync fails because the SSL cert issued has a common name associated with the internal domain. This is not a problem with OWA, as teh warning can just be clicked thorugh by users. It is ActiveSync which does not allow this. 
  
 I found a knowledge base article, [http://www.clickssl.com/]("http://support.microsoft.com/kb/931351")  
which shows a way to do this. By default, a CA that is configured on a Windows Server 2003-based domain controller does not issue certificates that contain the Subject Alternative Name (SAN) extension. If SAN entries are included in the certificate request, these entries are omitted from the issued certificate. To change this behavior, run the following commands at a command prompt on the server that runs the Certification Authority service. Press ENTER after each command. 
  
  
 certutil -setreg policy\EditFlags +EDITF_ATTRIBUTESUBJECTALTNAME2 
 net stop certsvc 
 net start certsvc  
  
I have completed this step on my Windows 2003 enterprise sub CA. I did not on my Windows 2003 standalone root CA, as it only issues one CA every two years to the enterprise Sub CA. 
  
  
 The rest of the article shows how to request the certificate via Web GUI, and also via certreq. Another source shows how to create a request using the "New-ExchangeCertificate" in the Exchange Management Shell. The Exchange Managmeent Shell method would seem to be the better way to go. 
  
Has anyone created a SSL cert with multiple SANs using an internal Windows 2003 enterprise subCA and could provide me with a detailed step-by-step or a web link? 
  
 Thanks in advance!

---

### Post by t0p on 2010-02-01
Is [this guide]("http://www.tc.umn.edu/%7Ebrams006/selfsign.html") no good?  Do a Google search for "how to create ssl ca" and it's the second result.  It looks pretty comprehensive to my untutored eye, but maybe I'm overlooking some deficiency?

---

