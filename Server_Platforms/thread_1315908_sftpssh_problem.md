---
title: "sftp/ssh problem"
date: 2009-11-05
forum: Server Platforms
---

### Post by ndnd on 2009-11-05
Hi,
I am farily new to linux. I have Ubuntu server 8.10 edition. For sercurity reasons my friend has setup ssh + key based access. This way anyone trying to ssh to the system needs the key. 
I can easily ssh using PUTTY to access however, SFTP is a problem. 

I would like to know the steps to reconfigure the SSH setting to default (so that no key is required) . I would like to do this only when I would like to SFTP data and then change the settings back to SSH + Key

from the forum it seems the most important file to edit is 

/etc/ssh/sshd_config 
My current files and settings in SSHD are 


> 
administrator@pacs08:/etc/ssh$ ls
moduli      sshd_config       ssh_host_dsa_key.pub  ssh_host_rsa_key.pub
ssh_config  ssh_host_dsa_key  ssh_host_rsa_key

administrator@pacs08:/etc/ssh$ sudo nano ssh_config
  GNU nano 2.0.7              File: ssh_config                        Modified


    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no




Also I compared with one sshd_config file and the only difference I saw was in my current system
> PasswordAuthentication no  

Default is commented out
> #PasswordAuthentication yes

Kindly let me know the exact changes as I am new
Thanks in advance for your help

---

### Post by undecim on 2009-11-05
What SFTP client are you using? There should be a way to set up keys with it.

Having password accessible SFTP would completely defeat the purpose of using public key authentication, because anyone who gets SFTP access to your account could just overwrite your authorized_keys files and use their key to log in.

You can, however, create another user for SFTP only. For this, log into your server (via putty) and run this command:```
useradd --shell /bin/false --create-home --comment "Password accessible SFTP for $USERNAME" $USERNAME-sftp
```Then, add some lines to the end of your sshd_config```
Match User username-sftp
    PasswordAuthentication yes
    AllowTcpForwarding no
```Where "username" is the username that you use to log into your server. You can edit the config file from putty by using the command "sudo nano /etc/ssh/sshd_config"

And finally, set the password for the new user```
sudo passwd $USERNAME-sftp
```Then, whenever you need to use your password to use SFTP, put "-sftp" at the end of your username

The caveat to this is that you won't be able to access your home directory, but you should still be able to store files with SFTP

---

### Post by ndnd on 2009-11-05
Thanks undecim for the detailed reply. All steps are very clear.  

I just wish to clarify (I will use an example) 

Typically the way ssh works is that I login remotely and am asked to verify the key etc. for the first time and then use username pwd. 

After this everytime I login since my key is already present it will ask for username and pwd. 

Fine - this works great with PUTTY, Filezilla. 

> 
Additional Security: 
My scenario - the system is extra secure. Meaning I have an additional key that I use for authentication 'every time' I login. It is a file that I keep on my client computer. When I use Putty. I have attached instructions on how I do it for clarity. 

This is what I wish to remove. I definitely wish to keep the default ssh which requires the key authentication. 

The reason for doing so is because I would like to use a GUI SFTP software lie Filezilla as I am not too familiar with command line and do not wish to make mistakes with files. :D

Thanks again in advance.

---

### Post by Lars Noodén on 2009-11-06
Filezilla should be able to use keys. YMMV

Edit->Settings->SFTP->Add keyfile

---

### Post by i.r.id10t on 2009-11-06
WinSCP should do it as well.

---

### Post by ndnd on 2009-11-06
Thanks Lars Noodén

I didn't know you could do that in Filezilla. However, when I tried to go to Settings->SFTP and select the file I got a message saying that the file is protected and has to be 'unprotected' so I wasn't sure if that is 'ok' 

Thanks i.r.id10t
For suggesting WinSCP. I prefer Filezilla so I would like to try with this in case it doesn't work then I will go with WinSCP

---

### Post by ndnd on 2009-11-06
Resolved!!

Filezilla had a small note at the bottom saying that Putty Paegent works with Filezilla. 

Never knew what was Paegent was until now!! 

So added the key with the Putty Paegent and was able to SFTP!! nice

---

