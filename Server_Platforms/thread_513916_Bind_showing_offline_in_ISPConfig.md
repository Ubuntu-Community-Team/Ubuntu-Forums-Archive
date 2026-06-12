---
title: "Bind showing offline in ISPConfig"
date: 2007-07-31
forum: Server Platforms
---

### Post by erito on 2007-07-31
Hey all,
anybody have any experience with ISPConfig showing Bind (Bind9) and only Bind being offline?  Everything else is just peachy in the eyes of my ISPConfig except Bind.  I can type my domain name into a browser on the physical server, and any tests by the bind tools (i.e rndc, host, dig) in terminal turn out normal.  I'm not sure if this would help but here are my results from netstat -tap:
> 
netstat -tap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 my.nameserver.com:60000  *:*                     LISTEN     5237/postgrey.pid - 
tcp        0      0 my.nameserver.com:2208   *:*                     LISTEN     5137/hpiod          
tcp        0      0 my.nameserver.com:10025  *:*                     LISTEN     22481/master        
tcp        0      0 *:mysql                 *:*                     LISTEN     7335/mysqld         
tcp        0      0 *:submission            *:*                     LISTEN     22481/master        
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     5758/smbd           
tcp        0      0 my.nameserver.com:spamd  *:*                     LISTEN     5242/spamd.pid      
tcp        0      0 *:www                   *:*                     LISTEN     21191/apache2       
tcp        0      0 *:ssmtp                 *:*                     LISTEN     22481/master        
tcp        0      0 *:81                    *:*                     LISTEN     21158/ispconfig_htt 
tcp        0      0 mydomain.com:domain    *:*                     LISTEN     30812/named         
tcp        0      0 my.nameserver.com:domain *:*                     LISTEN     30812/named         
tcp        0      0 *:ipp                   *:*                     LISTEN     3105/cupsd          
tcp        0      0 my.nameserver.com:953    *:*                     LISTEN     30812/named         
tcp        0      0 *:smtp                  *:*                     LISTEN     22481/master        
tcp        0      0 *:https                 *:*                     LISTEN     21191/apache2       
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     5758/smbd           
tcp6       0      0 *:imaps                 *:*                     LISTEN     5459/couriertcpd    
tcp6       0      0 *: pop3s                 *:*                     LISTEN     5505/couriertcpd    
tcp6       0      0 *: pop3                  *:*                     LISTEN     5475/couriertcpd    
tcp6       0      0 *:imap2                 *:*                     LISTEN     5436/couriertcpd    
tcp6       0      0 *:domain                *:*                     LISTEN     30812/named         
tcp6       0      0 *:ftp                   *:*                     LISTEN     21387/ftp: (acc 
tcp6       0      0 *:ssh                   *:*                     LISTEN     5784/sshd           
tcp6       0      0 *:ipp                   *:*                     LISTEN     3105/cupsd          
tcp6       0      0 ip6-localhost:953       *:*                     LISTEN     30812/named    
Anybody see anything out of the ordinary?   I'm reaching the conclusion that it may not be that Bind is offline, but I'm new to ISPConfig and Bind so I'm stumped.

erito

---

### Post by a9k on 2007-08-26
If ISPConfig is looking for the standard port to be open it isn't in your case:
cp 0 0 my.nameserver.com:953 *:* LISTEN 30812/named
Yours shows port 953 instead of 53

---

