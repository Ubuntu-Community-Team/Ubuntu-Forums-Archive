---
title: "openl2tp VPN connection"
date: 2013-01-30
forum: Server Platforms
---

### Post by deathadder on 2013-01-30
Hi all,

I'm trying to setup a openl2tp VPN connection with a combination of ippool, openl2tp, ppp and racoon. I've run into a strange (from my point of view) issue with regards to the IP address seen by the server.

I've got a Windows 7 host connecting to the machine and passing it's network traffic through the box, I can see DNS lookups in my logs:
> Jan 30 07:35:03 ajwebtest named[8391]: client 10.44.18.128#51745 (google.com): query: google.com IN A + (10.44.22.224)
Jan 30 07:35:03 ajwebtest named[8391]: client 10.44.18.128#51746 (google.com): query: google.com IN AAAA + (10.44.22.224)

However the IP seen in the logs is the actual IP address of the Windows 7 host and not the address given to the PPP connection...which seems strange to me. Would this be expected behaviour? If so, how do people work around iptable rules when the hosts address is never known before hand?

I've had to pick up this issue from someone else so don't know if additional software is required etc...but what I need to do is determine if the machine is coming in over the VPN connection and allow DNS requests for it and forward any HTTP(S) traffic on. Ideally I would like to be able to tie the connection up to the PPP address given to it (for various reporting reasons). Is this possible? 

ippool configuration:
```

pool create pool_name=default
pool address add pool_name=default first_addr=10.1.1.1 num_addrs=10 netmask=255.255.0.0
pool address reserve pool_name=default first_addr=10.1.1.1 num_addrs=1

```

racoon configuration:
```

path include "/etc/racoon";
path pre_shared_key "/etc/racoon/psk.txt";
path certificate "/etc/racoon/certs";

listen {
	isakmp 10.44.22.224 [500];
	isakmp_natt 10.44.22.224 [4500];
}

padding {
	maximum_length 20;	# maximum padding length.
	randomize off;		# enable randomize length.
	strict_check off;	# enable strict check.
	exclusive_tail off;	# extract last one octet.
}

remote anonymous {
	exchange_mode main, aggressive;
	doi ipsec_doi;
	situation identity_only;
	nat_traversal on;
	generate_policy on;
	proposal_check obey;
    	initial_contact off;
	passive on;
	nonce_size 16;
	send_cr off;
	send_cert off;

        proposal {
                # Win7 pararmeters.
                encryption_algorithm 3des;
                hash_algorithm sha1;
                authentication_method pre_shared_key;
                dh_group modp1024;
        }

        proposal {
                # WinXP pararmeters.
                encryption_algorithm 3des;
                hash_algorithm md5;
                authentication_method pre_shared_key;
                dh_group modp1024;
        }

        proposal {
                # Linux clients
                encryption_algorithm aes;
                hash_algorithm sha1;
                authentication_method pre_shared_key;
                dh_group modp1024;
        }

}

sainfo anonymous
{
	lifetime time 1 hour;
	encryption_algorithm aes, 3des;
	authentication_algorithm hmac_sha1, hmac_md5;
	compression_algorithm deflate;
}
```

openl2tp configuration:
```
tunnel profile modify profile_name=default \
	our_udp_port=1701 \

ppp profile modify profile_name=default \
	use_radius=no \
        auth_eap=no \
	auth_pap=no \
	auth_none=yes \
	auth_chap=yes \
	auth_mschapv1=yes \
	auth_mschapv2=yes \
	local_ipaddr=10.1.1.1 \
	dns_ipaddr_pri=10.44.22.224 \
	wins_ipaddr_pri=10.44.22.224 \
	ip_pool_name=default \
	proxy_arp=yes
```

---

