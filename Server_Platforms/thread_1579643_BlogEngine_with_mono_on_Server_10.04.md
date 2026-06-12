---
title: "BlogEngine with mono on Server 10.04"
date: 2010-09-22
forum: Server Platforms
---

### Post by KommerszUnicum on 2010-09-22
[B]Dear Friends!
[/B]
I'm trying to configure the BlogEngine.NET blog to use it with mono on my server but I've encountered an issue with it.

I've installed mono and the ASP.NET 2.0 samples are running in it correctly, but when I setup an application for the blogengine the browser displays the following error:

**Server Error in '/blog' Application**

   ***'system.web' is expected Line 59, position 6.***

 **Description: **HTTP 500. Error processing request.
 **Stack Trace: **
    System.Xml.XmlException: 'system.web' is expected  Line 59, position 6. 

at Mono.Xml2.XmlTextReader.Expect (System.String expected) [0x00000]    
at Mono.Xml2.XmlTextReader.ReadEndTag () [0x00000]    at Mono.Xml2.XmlTextReader.ReadContent () [0x00000]    at Mono.Xml2.XmlTextReader.Read () [0x00000]    at System.Xml.XmlTextReader.Read () [0x00000]    at System.Xml.XmlReader.Skip () [0x00000]    
at System.Xml.XmlTextReader.Skip () [0x00000]    
at System.Configuration.SectionGroupInfo.ReadContent (System.Xml.XmlReader reader, System.Configuration.Configuration config, Boolean overrideAllowed, Boolean root) [0x00000]    
at System.Configuration.SectionGroupInfo.ReadData (System.Configuration.Configuration config, System.Xml.XmlReader reader, Boolean overrideAllowed) [0x00000]    
at System.Configuration.SectionGroupInfo.ReadContent (System.Xml.XmlReader reader, System.Configuration.Configuration config, Boolean overrideAllowed, Boolean root) [0x00000]    
at System.Configuration.SectionGroupInfo.ReadRootData (System.Xml.XmlReader reader, System.Configuration.Configuration config, Boolean overrideAllowed) [0x00000]    
at System.Configuration.Configuration.ReadConfigFile (System.Xml.XmlReader reader, System.String fileName) [0x00000]    at System.Configuration.Configuration.Load () [0x00000] 
   at System.Configuration.Configuration.Init (IConfigSystem system, System.String configPath, System.Configuration.Configuration parent) [0x00000]    at System.Configuration.Configuration..ctor (System.Configuration.InternalConfigurationSystem system, System.String locationSubPath) [0x00000]    
at System.Configuration.InternalConfigurationFactory.Create (System.Type typeConfigHost, System.Object[] hostInitConfigurationParams) [0x00000]    
at System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration (System.String path, System.String site, System.String locationSubPath, System.String server, System.String userName, System.String password, Boolean fweb) [0x00000] 

**Version information: **Runtime: Mono 2.4.4; ASP.NET  Version: 2.0.50727.1433 

I have no idea what is wrong. The application was set with the standard mono-server2-admin and mono-server2-update. The conf file is the following for this application in the /etc/mono-server2/conf.d/blog/

10_blog:

This is the configuration file 
for the blog virtualhost
path = /var/www/blog
alias = /blog
libs = /usr/lib/mono/2.0
vhost = localhost
port = 80 

Do you have any idea?

Thank you for you help!

Regards,
KommerszUnicum

---

### Post by directhex on 2010-09-23
It looks like BlogEngine.NET has some case sensitivity bugs - there is no such thing as system.web, but there IS a System.Web

Either work out where they've typo'd on case & fix it (and send a patch upstream), or look in the mod_mono documentation on how to set the environment variable MONO_IOMAP=all so Mono tries to fake its way out of case sensitivity bugs

---

