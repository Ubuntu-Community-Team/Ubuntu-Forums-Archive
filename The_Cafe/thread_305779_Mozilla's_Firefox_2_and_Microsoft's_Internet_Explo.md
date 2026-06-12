---
title: "Mozilla's Firefox 2 and Microsoft's Internet Explorer 7 flaw!"
date: 2006-11-23
forum: The Cafe
---

### Post by John.Michael.Kane on 2006-11-23
Have a read [http://news.com.com/2100-1002_3-6137844.html](http://news.com.com/2100-1002_3-6137844.html)

---

### Post by RAV TUX on 2006-11-23
> **SD-Plissken said:**
> Have a read [http://news.com.com/2100-1002_3-6137844.html](http://news.com.com/2100-1002_3-6137844.html)

interesting read:

> **    Firefox, IE vulnerable to fake login pages?**

   Flaw could enable attackers to compromise usernames and passwords, security researcher warns, citing exploit on MySpace. 
 By                                                 Tom Espiner                                                       
                        Special to CNET News.com
                                                                         
       Published: November 22, 2006, 7:09 AM PST    
           
     
  
                         **Mozilla's Firefox 2 and Microsoft's Internet Explorer 7 are vulnerable to a flaw that could allow attackers to steal passwords.** 
 Dubbed a reverse cross-site request, or RCSR, vulnerability by its discoverer, Robert Chapin, the flaw lets hackers compromise users' passwords and usernames by presenting them with a fake login form. Firefox Password Manager will automatically enter any saved passwords and usernames into the form. 
 The data is then automatically sent to an attacker's computer without the user's knowledge, according to the [Chapin Information Services]("http://www.info-svc.com/") site.  
 An exploit for this flaw has already been seen on social-networking site MySpace.com, and it could affect anyone using a blog or forum that allows user-generated HTML code to be added, according to Chapin. 
 "Users of both Firefox and Internet Explorer need to be aware that their information can be stolen in this way when visiting blog and forum Web sites at trusted addresses," Chapin said. 
 According to security company [Netcraft]("http://news.netcraft.com/"), which discovered the exploit being used on MySpace, a fraudulent login page was hosted on the company's own servers.  
 As the page did not exhibit any signs of external content, such as cross-site scripting (XSS) or open redirects, it is "convincing, and even security-conscious users are at risk of becoming victims," CIS said. 
 The attack was launched from a profile page, and it used specially crafted HTML to hide the genuine MySpace content from the page and instead display its own login form. 
 According to Chapin, an RCSR attack is much more likely to succeed than an XSS attack because neither Internet Explorer nor Firefox is designed to check the destination of form data before the user submits them. The browser doesn't sound an alarm because the exploit is conducted at the trusted Web site. 
                   

           Two weeks ago, CIS reported to Mozilla that the Firefox Web browser will automatically fill saved usernames and passwords into RCSR forms. Attacks are more likely to succeed in Firefox because Internet Explorer will not automatically fill in saved usernames and passwords, unless the RCSR form appears on the same page as a legitimate login form. 
 No fix had been issued by Mozilla at the time of writing, though a bug report has been filed. The organization is reportedly working on a fix for Firefox 2, but it's not clear whether earlier versions are also affected. Security company Secunia has advised users to disable the "Remember passwords for sites" option in Firefox preferences. 
 To take advantage of the flaw, a malicious hacker would have to create a fake login form on a trusted Web site. CIS has recommended that all Webmasters review their server code for the possibility of XSS and RCSR injections, especially operators of encrypted Web sites. 
 "These attacks could be highly effective against firewalled local network servers and HTTPS addresses that are not otherwise accessible because the attacker does not need direct access," the CIS site said. 
 *Tom Espiner of [ZDNet UK]("http://news.zdnet.co.uk/") reported from London.*

I am curious is the vulnerability also true with Opera, Epiphany or Konqueror?

---

