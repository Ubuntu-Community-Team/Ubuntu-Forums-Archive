---
title: "Scritp to wait for few seconds before executing next line"
date: 2010-09-29
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-29
I have a script which copies(scp) .war file to tomcat's webapps and the .war file extracts creating a folder under webapps directory on a ubuntu system. My next line of the script is restarting the tomcat which is executed immediately before the .war is extracted and this causing problem with



Is it possible so that it waits for few seconds/minutes before it executes the next line of the script. The script is of normal ubuntu commands.

---

### Post by the_original_billq on 2010-09-29
> **Thyagaraj said:**
> I have a script which copies(scp) .war file to tomcat's webapps and the .war file extracts creating a folder under webapps directory on a ubuntu system. My next line of the script is restarting the tomcat which is executed immediately before the .war is extracted and this causing problem with



Is it possible so that it waits for few seconds/minutes before it executes the next line of the script. The script is of normal ubuntu commands.

sleep n

where n is in seconds...

---

### Post by Thyagaraj on 2010-10-01
Thank you!:)

---

