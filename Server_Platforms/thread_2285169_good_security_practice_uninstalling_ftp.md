---
title: "good security practice: uninstalling ftp"
date: 2015-07-03
forum: Server Platforms
---

### Post by Drone4four on 2015-07-03
I can't figure out how to uninstall ftp. I thought I removed it months ago. Today when I type 'apt-get remove ftp ftpd' as su on my server, the output tells me these two packages are not installed. But in my local Konqueror ftp client, when I enter ftp://[user]@[remotehost]/home/[user] into the address bar, it prompts me for a user name and password - - which I enter - - and voila, I am accessing my server via ftp. It's dangerous to have ftp working like this, am I right?

When I enter, 'apt-get remove ftp*' an enormous list of packages scroll my terminal saying that such and such a package “is not installed, so not removed”. But at the very bottom it asks do you wish to remove openssh-server openssh-sftp-server vsftpd which are the only three packages which involve ftp that are installed on my server. I press 'n' because these are secure packages.

So why is my server still accessible by ftp?

---

### Post by papibe on 2015-07-03
Hi  Drone4four.
> **Drone4four said:**
> openssh-server openssh-sftp-server vsftpd
From that list, vsftpd is the only package related to ftp. ssh and sftp are completely different things.

If 'vsftpd' is installed, configured and running, it means the server is providing ftp services. Uninstall it if you don't want ftp access.

Hope it helps. Let us know how it goes.
Regards.

BTW, IMHO vsftpd is only secure when properly set up (see [here]("https://help.ubuntu.com/community/vsftpd") and [here]("https://www.digitalocean.com/community/tutorials/how-to-configure-vsftpd-to-use-ssl-tls-on-an-ubuntu-vps")).

---

### Post by CharlesA on 2015-07-04
vsftpd is an ftp service. You wouldn't have any issues having a regular FTP client installed though.

Best practice imo is to just stick to sftp since it is included with openssh-server.

---

### Post by Drone4four on 2015-07-04
[The DigitalOcean guide that **papibe** linked to]("https://www.digitalocean.com/community/tutorials/how-to-configure-vsftpd-to-use-ssl-tls-on-an-ubuntu-vps") concludes with these remarks: > This setup improves the security of FTP, but it still suffers from insecurity when establishing a connection. If at all possible, it is better to switch to SFTP for these kinds of operations. However, if you do decide to go with FTP, you should make sure to use TLS/SSL whenever possible.  What the author of this guide is concluding is that as compared sftp, regular ftp is insecure (even with taking precautions such as carefully configuring and using TLS/SSL).  **CharlesA** suggests that sftp is included in the openssh-server package.  But even with openssh-server, I couldn’t access my remote file tree with sftp.  So I installed a package called sftpcloudfs, which is basically some advanced utilities which are python based.  Now I can access my server via sftp just fine and not have to worry about a cyberpunk script kiddie from exploiting the weaknesses in ftp.  ftp doesn’t work now and sftp does. So I think I’ve resolved my issue and accomplished what I set out to do.  

I have one further query.  **CharlesA** said that: >  You wouldn't have any issues having a regular FTP client installed though.  Are you saying that it its ok to have ftp installed and not have to worry about its inherent weaknesses? I intend on keeping ftp uninstalled now, but if I did still have installed, then that still wouldn't pose a significant security risk?

---

### Post by papibe on 2015-07-05
> **Drone4four said:**
> Are you saying that it its ok to have ftp installed and not have to worry about its inherent weaknesses?
A few extra thoughts:

There are 2 traditional ftp packages:
[LIST]
[*]ftp - classical file transfer client
[*]ftpd - File Transfer Protocol (FTP) server
[/LIST]
Having installed the ftp client, as CharlesA said, does not produce security risks for the server in the sense that:
[LIST]
[*]it does not open ports.
[*]it does not run in the background as a service.
[*]it does not receive any kind of external (network) or internal (loopback) connections.
[/LIST]
The only potential problem would be if you ftp from your server to another remote server. In this case you would be creating a risk on the remote server, not yours directly. Mainly, you could:
[LIST]
[*]expose your ftp credentials on the remote server.
[/LIST]
Regardless, there a side effect that should be considered. Although this situation won't bounce back to an experienced admin, 'casual' server admins can often reuse passwords, usernames, credentials, etc. and that could potentially create a risk.

Does that help?
Regards.

---

### Post by CharlesA on 2015-07-05
> **Drone4four said:**
> [The DigitalOcean guide that **papibe** linked to]("https://www.digitalocean.com/community/tutorials/how-to-configure-vsftpd-to-use-ssl-tls-on-an-ubuntu-vps") concludes with these remarks:   What the author of this guide is concluding is that as compared sftp, regular ftp is insecure (even with taking precautions such as carefully configuring and using TLS/SSL).  **CharlesA** suggests that sftp is included in the openssh-server package.  But even with openssh-server, I couldn’t access my remote file tree with sftp.  So I installed a package called sftpcloudfs, which is basically some advanced utilities which are python based.  Now I can access my server via sftp just fine and not have to worry about a cyberpunk script kiddie from exploiting the weaknesses in ftp.  ftp doesn’t work now and sftp does. So I think I’ve resolved my issue and accomplished what I set out to do.

As long as you ensure openssh is secure, you should be fine.  See here: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

> I have one further query.  **CharlesA** said that:   Are you saying that it its ok to have ftp installed and not have to worry about its inherent weaknesses? I intend on keeping ftp uninstalled now, but if I did still have installed, then that still wouldn't pose a significant security risk?

I think papibe covered the main posts, but basically, the ftp client isn't listening for connections, it is the thing that makes connections to other ftp servers, so there is little security risk to having it installed.

---

### Post by SeijiSensei on 2015-07-05
Most browsers include support for ftp:// URLs.  There really isn't any security threat from your having the client-side code in a browser, or even the command-line ftp client on your machine.  As a server service, FTP is insecure because it requires sending login credentials in clear-text.  But simply having FTP clients on a desktop machine isn't really a vulnerability any more than having a browser is one.  If you don't use the FTP services the browsers offer, there's no threat at all.

---

