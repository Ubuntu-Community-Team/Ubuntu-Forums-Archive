---
title: "howto: setup openvpn on ebox 1.4"
date: 2010-04-22
forum: Server Platforms
---

### Post by senor_smile on 2010-04-22
I am writing this little howto based off of the information presented in ebox's screencast.  Unfortunately, and this may be simply because of how thick I am, when following their documentation to set up openvpn, I could never get it functioning.  These are the steps I took following that screencast to get it working.  *_No warranty is given or implied that the following directions will work for you.  _*

**Enable VPN module (daemon)**
```
1. Select *Module Status* on the left
2. find VPN in the list and select the checkmark
3. *If a window telling you what changes that will be made pops up, click accept*
```

**Create Certification Authority Certificate **
```
1. Select *Certification Authority -> General * on the left
2. Fill out organization name, country code, city, state, days to expire (I inserted 3650)
3. Click Create
```

Now, you should see a window with headings
[I]Issue a New Certificate
Current Certificate List[/I]

**Issue a New Server Certificate** (Create a specific certificate for this instance of the vpn server)
```
1. Fill out Common name (e.g. hq.mycompany.com) and days to expire (e.g. 1825) 
    [I](According to ebox, this should be the "external host name for your office." 
    I don't know that it really matters.  My office just has an IP address, 
    no host name, and this set up works just fine.)  [/I]
2. Click Issue. 

```

**Create new client certificates(users)**
```

1. Fill out common name and days to expire for client computer
2. Click Issue
[I]3. Repeat for as many clients as you'd like to set up.  You can always come 
back here and set up more clients in the future.  [/I]

```

**Create the VPN server**
```
1. Select *VPN -> Server* on the left. 
2. Click Add New
3. DON'T click Enable
4. Enter the name for the vpn server (e.g. hqvpn)
5. click Add
```

**Configure the VPN Server**
```
1. Click the icon beneath Configuration that corresponds to the new VPN server 
    (labeled e.g. hqvpn)
2. Fill out VPN Address (if you want to change it from what it chooses)
3. Select the server certificate (e.g. hq.mycompany.com)
4. Enable Network Address Translation if this is NOT the Router/Gateway for your network.  
5. Click Allow client-to-client connections if you'd like to enable this.  
6. Click Change.
```

**Save Changes**
```
1. Click on *Save Changes* in the upper right hand corner. 
2. Click Save
```

The VPN server is now enabled.  Next, we need to download the certificate files for our client(s).

**Download client certificate files**
```

1. Select *VPN -> Server* on the left.
2. Click the icon under Download client bundle
3. Select the client type (i.e. windows or linux)
4. Select the client certificate (e.g. joesmachine)
5. Put a check in Add OpenVPN's installer to bundle if needed
    *for Windows clients only*
6. Enter the server Address (the public domain name or I.P. address needed
    to reach the server from the internet.  
7. Click change. 

```

This will automatically download the client files in zip format.  Repeat for as many clients as you have created.  

Install the client files into the openvpn configuration file directory on the client machine 
(Windows: C:\Program Files\OpenVPN\config   
Linux: /etc/openvpn/ )

---

