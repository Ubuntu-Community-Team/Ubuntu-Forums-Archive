---
title: "How to change docBase of Tomcat 8.5.13"
date: 2020-04-17
forum: Server Platforms
---

### Post by deepakdeshp on 2020-04-17
[COLOR=#333333]Hello,[/COLOR]
      
      [COLOR=#333333]Tomcat is        running on my virtual Ubuntu server 18.04. The settings  is        default which was created during install. tomcat is installed in        /opt/tomcat .[/COLOR]
      [COLOR=#333333]My daughter        has installed a Tomcat application on the dual boot Windows , the Win partition is accessible from my Ubuntu server. I want to access the        application installed in Windows from Ubuntu Tomcat. How do I do that?[/COLOR]
      
      [COLOR=#333333]Thanks for        any replies.[/COLOR]

---

### Post by CelticWarrior on 2020-04-17
Virtualization is not dual-boot.
And [Apache Tomcat]("https://en.wikipedia.org/wiki/Java_Servlet") *(sometimes simply "Tomcat") is an [open-source]("https://en.wikipedia.org/wiki/Open-source_software") implementation of the [Java Servlet]("https://en.wikipedia.org/wiki/Java_Servlet"), [JavaServer Pages]("https://en.wikipedia.org/wiki/JavaServer_Pages"), [Java Expression Language]("https://en.wikipedia.org/wiki/Unified_Expression_Language") and [WebSocket]("https://en.wikipedia.org/wiki/WebSocket") technologies.[SUP][[3]]("https://en.wikipedia.org/wiki/Apache_Tomcat#cite_note-3")[/SUP] Tomcat provides a "pure [Java]("https://en.wikipedia.org/wiki/Java_(programming_language)")" [HTTP]("https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol") [web server]("https://en.wikipedia.org/wiki/Web_server") environment in which [Java]("https://en.wikipedia.org/wiki/Java_(programming_language)") code can run.* 

So, you probably meant a "Java app"? Something you'd run from the folder containing it? What exactly is the problem?

---

### Post by deepakdeshp on 2020-04-18
> **CelticWarrior said:**
> Virtualization is not dual-boot.
And [Apache Tomcat]("https://en.wikipedia.org/wiki/Java_Servlet") *(sometimes simply "Tomcat") is an [open-source]("https://en.wikipedia.org/wiki/Open-source_software") implementation of the [Java Servlet]("https://en.wikipedia.org/wiki/Java_Servlet"), [JavaServer Pages]("https://en.wikipedia.org/wiki/JavaServer_Pages"), [Java Expression Language]("https://en.wikipedia.org/wiki/Unified_Expression_Language") and [WebSocket]("https://en.wikipedia.org/wiki/WebSocket") technologies.[SUP][[3]]("https://en.wikipedia.org/wiki/Apache_Tomcat#cite_note-3")[/SUP] Tomcat provides a "pure [Java]("https://en.wikipedia.org/wiki/Java_(programming_language)")" [HTTP]("https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol") [web server]("https://en.wikipedia.org/wiki/Web_server") environment in which [Java]("https://en.wikipedia.org/wiki/Java_(programming_language)") code can run.* 

So, you probably meant a "Java app"? Something you'd run from the folder containing it? What exactly is the problem?

Thanks for the reply. I have Windows as dual boot with Mint19.3. I have Ubuntu server 18.04 as the guest with Mint as the host using vmware workstation 15.
Tomcat is installed in the server and can be accessed from the VM host mint in a browser. A Java app is installed in Windows and can be ascessed in Windows when I boot into it.
I am trying to access the Windows Tomcat application from my Ubuntu server. I have access to Windows partition from the VM server through the host Mint 19.

---

