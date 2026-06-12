---
title: "[HOWTO] Test your SSL cert for insecure ciphers"
date: 2012-01-16
forum: Security
---

### Post by kevpatts on 2012-01-16
Hey all,

I often have to test remote SSL certs for insecure ciphers for PCI DSS reasons and have a script to do it that works in 11.10 (scripts for older distros don't work cause of changes in OpenSSL):
```
#!/bin/bash

if ! [ $1 ];
then
	echo syntax: $0 host [-v]
	exit
fi

if [ "$2" == "-v" ];
then
	verbose=true
fi

# OpenSSL requires the port number.
SERVER=$1:443
DELAY=0
ciphers=`openssl ciphers 'ALL:eNULL' | sed -e 's/:/ /g'`

echo Obtaining cipher list from `openssl version`.

for cipherLine in `openssl ciphers -v | awk '{print $1,":: "$5}' | sed -e "s/ :: Enc=[^(]*(/,/" -e "s/)$//"`;
do
	cipher=`echo $cipherLine | sed "s/,.*//"`
	bits=`echo $cipherLine | sed "s/[^,]*,//"`
	result=`echo -n | openssl s_client -cipher "$cipher" -connect $SERVER 2>&1`
	if [[ "$result" =~ "Cipher is $cipher" ]] ; then
		echo "$cipher ($bits bits)... YES"
	else
		if [[ $verbose == true ]] ; then
			if [[ "$result" =~ "Cipher is (NONE)" ]] ; then
				error=`echo -n $result | cut -d':' -f6`
				echo "$cipher ($bits bits)... NO ($error)"
			else
				echo "$cipher ($bits bits)... UNKNOWN RESPONSE"
			fi
		fi
	fi
	sleep $DELAY
done
```

By PCI DSS you shouldn't have any ciphers less than 128 bits enabled. To ensure this is true in Apache2 you need to set the following settings in your main config file (normally apache2.conf or httpd.conf):
```
SSLProtocol -ALL +SSLv3 +TLSv1
SSLCipherSuite ALL:!aNULL:!ADH:!eNULL:!LOW:!EXP:RC4+RSA:+HIGH:+MEDIUM
```

Hope this is useful.

---

