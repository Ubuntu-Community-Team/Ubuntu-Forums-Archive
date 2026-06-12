---
title: "Ubuntu Server - Problem With Network Configuration"
date: 2011-04-28
forum: Server Platforms
---

### Post by flyingsuperhigh on 2011-04-28
Hey,

I have installed Ubuntu Server on an old desktop, however, I am experiencing issues connecting to my network. I am using a D-Link gwl-122 USB adapter to connect to my network. My network has the following security configurations: wpa-personal (security-type), tkip (encryption-type), and internet connection is DHCP. During the Ubuntu Server installation process, I was only given the option to enter the wep key and hence I skipped the network configuration process. Now that I've completed the installation, I'm not quite sure what to do. I know that the USB network adapter works because I successfully connected to the internet with it when I was using windows XP. I cannot really have a wired connection straight from my router because there is a problem with my network card. I would like my server to be connected to the internet since I want to SSH into it and do other activities like hosting my personal website. Anybody have any suggestions of what I should do to successfully connect my server to the internet using my usb network adapter.

---

### Post by volkswagner on 2011-04-28
To verify your wireless device is working, with proper drivers run the following.

```
iwconfig
```

If you see your card listed as eth1, wlan0 or similar, you should be ready to configure.  If you get " no wireless extensions" you have some configuring to do and need to post the output of:

```
lsusb
```

check [this post]("http://ubuntuforums.org/showthread.php?t=1734823") for more help if you card is working.

---

### Post by flyingsuperhigh on 2011-04-28
Firstly thanks for the reply. 

Here's the output which I received when I typed in the command iwconfig:

lo - no wireless extensions

eth0 - no wireless extensions

wlan 0 - 
IEEE 802.11bg ESSID:"my_essid_name"
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management: on

Next, when I typed in the command that you suggested in the other post:
sudo iwconfig eth0 essid nameofwifi key xxxxsecuritykeyxxxx (I made the appropriate substitutions) I get the following output:
Error for wireless request "Set Encode" (8B2A):
invalide argument "my_password".

Now I know that the password is right but I'm still not able to connect. Any suggestions.

---

### Post by volkswagner on 2011-04-28
> **flyingsuperhigh said:**
> Firstly thanks for the reply. 

Here's the output which I received when I typed in the command iwconfig:

lo - no wireless extensions

eth0 - no wireless extensions

wlan 0 - 
IEEE 802.11bg ESSID:"my_essid_name"
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management: on

Next, when I typed in the command that you suggested in the other post:
sudo iwconfig eth0 essid nameofwifi key xxxxsecuritykeyxxxx (I made the appropriate substitutions) I get the following output:
Error for wireless request "Set Encode" (8B2A):
invalide argument "my_password".

Now I know that the password is right but I'm still not able to connect. Any suggestions.

....EDIT

oops I went too fast.  

What is the output of 
```
lsusb
```

Perhaps the security protocol is not supported in linux on your adapter?

Are you trying to use passphrase or the actual key?

This is a little beyond my expertise.  Wifi security models that is.

Do you have wpa_supplicant installed?

```
wpa_supplicant -v
```

---

### Post by flyingsuperhigh on 2011-04-29
Okay so I went out an bought a new network card and installed it into my computer. I was successfully able to connect to the network and it works now. However, now I want to ssh into my server and I am using putty for this. I have installed openssh server and client. Nonetheless, I keep getting a network error: connection timed out message. I determined the public ip of my server using the following command:

curl -s checkip.dyndns.org | sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

Once I figured out my IP I typed the following information into putty: my_username@server's_public_ip_address. The problem is that I keep getting error messages. 

Any ideas?

---

### Post by volkswagner on 2011-04-29
Are you able to connect via ssh locally (LAN) using local ip address?

Do you have the correct port opened on the router where your server resides?

```
cat /etc/ssh/sshd_config | grep Port

```

Do you have Ubuntu Firewall running on the server?

```
sudo ufw status
```

---

### Post by flyingsuperhigh on 2011-04-30
Once again thank you for helping me thus far. I am using Port 22 and I believe the firewall status is inactive. I think the issue is the Port 22, I am not sure what to do with this. Is it some configuration changes which I must make on the server? Or is it some configuration changes which I must make on my router?

---

### Post by volkswagner on 2011-04-30
Repeat: **Are you able to ssh local on the lan with the internal ip address?**

If you are trying from outside your lan or using public ip, you need to forward/open port 22 on your router to the ip (LAN) address of your server.

You also need to verify that your ISP does not block port 22.  You can check this from inside your lan after forwarding port 22 on the router.  You can the navigate to canyouseeme.org and check port 22 from any pc inside your lan.

---

### Post by flyingsuperhigh on 2011-04-30
Firstly, yes I am able to ssh from a local computer to the server.

Next, I've also forwarded port 22 to the LAN address of the router.

When I navigate to canyouseeme.org I don't think I am getting the results that I want as I am getting the following message:

Error: I could not see your service on public_ip_address_of_one_of_the_local_computers on port (22)
Reason: Connection timed out.

What's next?

---

### Post by volkswagner on 2011-04-30
> **flyingsuperhigh said:**
> Firstly, yes I am able to ssh from a local computer to the server.

Next, I've also forwarded port 22 to the [COLOR="Olive"]LAN address of the router[/COLOR].

When I navigate to canyouseeme.org I don't think I am getting the results that I want as I am getting the following message:

Error: I could not see your service on public_ip_address_of_one_of_the_local_computers on port (22)
Reason: Connection timed out.

What's next?

I will assume the above is a typo.  You should be forwarding port 22 to the ip of your server:

The following will get you your lan ip.
```
ifconfig
```

If you are confident the forward is correct, then most likely your isp blocks port 22.

You will then need to scan for open ports and run ssh on an alternate port.

You can temporarily open a large port range forwarded to your server, then check canyouseeme.org for open ports in that range.

Sorry I don't have a more elegant solution.

If you believe your isp should not be blocking port 22 you can contact them directly.

---

### Post by flyingsuperhigh on 2011-04-30
I just had a question. Presently, I am not using any static IPs. Do you think this would be a reason why it's not working? If yes, would I need to make changes on my router to assign static IPs or on the individual computers?

Thanks, once again.

---

### Post by volkswagner on 2011-04-30
> **flyingsuperhigh said:**
> I just had a question. Presently, I am not using any static IPs. Do you think this would be a reason why it's not working? If yes, would I need to make changes on my router to assign static IPs or on the individual computers?

Thanks, once again.

It could be a problem only  if you forwarded port 22, then the server ip changed.

I is always best to have your server on a static ip address.  In my opinion it is best if you can assign the static ip based on mac address of you network card via your router settings.  This approach can handle local dns at the router level on your LAN.  

Again if you run:

```
ifconfig
```

On your server, and the ip address matches the ip you forwarded port 22 to, then most likely the problem is blocked port by your ISP.

---

### Post by hawk2010 on 2011-05-02
If you are running an ssh server and want to connect from outside. Yes you need to have an internal static IP address as well as a static Public IP unless you got dyndns. You can define your static settings like this  . Also you have to port forward port 22 or if you are running ssh on another port to this static IP address. after you do the below config you have to do /etc/init.d/networking restart

iface yourinterface inet static
        address         xxx.xxx.xxx,xxx
        netmask         xxx.xxx.xxx,xxx
        broadcast       xxx.xxx.xxx,xxx
        network         xxx.xxx.xxx,xxx
        gateway         xxx.xxx.xxx,xxx

---

