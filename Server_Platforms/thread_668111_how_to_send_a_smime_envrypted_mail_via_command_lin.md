---
title: "how to send a smime envrypted mail via command line"
date: 2008-01-15
forum: Server Platforms
---

### Post by Tex-Twil on 2008-01-15
Hello,
using  OpenSSL, I create a smime encrypted mail with a public key:

```

openssl smime -encrypt  -in my-message.txt -from you@youraddress.com -to her@heraddress.com -subject 'My encrypted reply' thunder_pub.pem > mail.msg

```

The mail.msg contains the email:
```

To: her@heraddress.com
From: you@youraddress.com
Subject: My encrypted reply
MIME-Version: 1.0
Content-Disposition: attachment; filename="smime.p7m"
Content-Type: application/x-pkcs7-mime; smime-type=enveloped-data; name="smime.p7m"
Content-Transfer-Encoding: base64

MIIBkQYJKoZIhvcNAQcDoIIBgjCCAX4CAQAxggFEMIIBQAIBADCBqDCBmjELMAkG
A1UEBhMCREUxDzANBgNVBAgTBkJlcmxpbjEPMA0GA1UEBxMGQmVybGluMRMwEQYD
VQQKEwpaZXJ0aWZpY29uMQwwCgYDVQQLEwNSTkQxGTAXBgNVBAMTEFRodW5kZXJi
aXJkIFVzZXIxKzApBgkqhkiG9w0BCQEWHGVuZ2luZVRodW5kZXJAemVydGlmaWNv
bi5jb20CCQDtQjRP4bxwcTANBgkqhkiG9w0BAQEFAASBgDxa4oeNRRJG3moLv2Wp
HG9Ho0VP8Ds45XBZDs5S4eh8gDf3QxjG6noKe4XYQUrsGJrk1A3iK6DyfAuzgzaV
WoB/r8D1K1k/xV65/NiQ2lxkLkL0eDxW0V5FbOT5LR5dZ16iyFqyH2QH8AmTDhge
JZkgq4FYZ2K0gc8q3majyZufMDEGCSqGSIb3DQEHATAaBggqhkiG9w0DAjAOAgIA
oAQIONvL0IVPNzaACIYEhMcVynB6


```

I would like to send this file/email via a command line to my SMTP server. I tried [swaks]("http://www.jetmore.org/john/code/#swaks")  but I dont know how to set the correct Content-Type field to application/x-pkcs7-mime so that the mail is recognized as encrypted,

Thanks for your help
Regards,
Tex

---

### Post by Tex-Twil on 2008-01-15
Ok it I've found the swaks option where I can specify the Content-Type option.

```
--header "Content-Type: application/x-pkcs7-mime; smime-type=enveloped-data; name="smime.p7m""
```

Then I just need to set the body of the email to contain the encrypted email and it works correctly.

---

### Post by Tex-Twil on 2008-01-17
Hello again,
the above solution works for an encrypted email but it is more tricky for a signed email since the header of a signed email changes from one email to another. My question is if there is a email script which can parse a file containing this signed email:

```

To: [email]batman@zertificon.com[/email]
From: [email]robin@email.com[/email]
Subject: Signed email ;)
MIME-Version: 1.0
Content-Type: multipart/signed; protocol="application/x-pkcs7-signature"; micalg=sha1; boundary="----1ABC9146925AEBE03F7FA2757971449C"

This is an S/MIME signed message

------1ABC9146925AEBE03F7FA2757971449C
This is my email body ;)

------1ABC9146925AEBE03F7FA2757971449C
Content-Type: application/x-pkcs7-signature; name="smime.p7s"
Content-Transfer-Encoding: base64
Content-Disposition: attachment; filename="smime.p7s"

MIIGHQYJKoZIhvcNAQcCoIIGDjCCBgoCAQExCzAJBgUrDgMCGgUAMAsGCSqGSIb3
DQEHAaCCA9wwggPYMIIDQaADAgECAgkA6wuANug7V1AwDQYJKoZIhvcNAQEFBQAw
gaAxCzAJBgNVBAYTAkRFMRUwEwYDVQQIEwxCcnRsaW4gU3RhdGUxDzANBgNVBAcT
BkJlcmxpbjETMBEGA1UEChMKWmVydGlmaWNvbjEMMAoGA1UECxMDUk5EMR0wGwYD
VQQDExRUaHVuZGVyYmlyZCBFeHRlcm5hbDEnMCUGCSqGSIb3DQEJARYYdGh1bmRl
cmJpcmRAZXh0ZXJuYWwuY29tMB4XDTA4MDExNTE1MzQyMVoXDTA4MDIxNDE1MzQy
MVowgaAxCzAJBgNVBAYTAkRFMRUwEwYDVQQIEwxCcnRsaW4gU3RhdGUxDzANBgNV
BAcTBkJlcmxpbjETMBEGA1UEChMKWmVydGlmaWNvbjEMMAoGA1UECxMDUk5EMR0w
GwYDVQQDExRUaHVuZGVyYmlyZCBFeHRlcm5hbDEnMCUGCSqGSIb3DQEJARYYdGh1
bmRlcmJpcmRAZXh0ZXJuYWwuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKB
gQC7Ja0QeeHG76qwHITowsE/7CMAATNW6oTRteg3Imj6LKIz1a/diWFyqM1RdoGe
mDtLzSj44JqjWjql3oGiv6tFVx2b4hLGmXM3mOooAIlhZmuX0jJuNC4yefNUcPH/
Ysm7BlYclAwIR/nauv8tvRQMM3brIJ93aP5KLw+ZqJc/owIDAQABo4IBFjCCARIw
HQYDVR0OBBYEFEez8iPlz4xMaA1nKqWef/AsgY2eMIHVBgNVHSMEgc0wgcqAFEez
8iPlz4xMaA1nKqWef/AsgY2eoYGmpIGjMIGgMQswCQYDVQQGEwJERTEVMBMGA1UE
CBMMQnJ0bGluIFN0YXRlMQ8wDQYDVQQHEwZCZXJsaW4xEzARBgNVBAoTClplcnRp
Zmljb24xDDAKBgNVBAsTA1JORDEdMBsGA1UEAxMUVGh1bmRlcmJpcmQgRXh0ZXJu
YWwxJzAlBgkqhkiG9w0BCQEWGHRodW5kZXJiaXJkQGV4dGVybmFsLmNvbYIJAOsL
gDboO1dQMAkGA1UdEwQCMAAwDgYDVR0PAQH/BAQDAgXgMA0GCSqGSIb3DQEBBQUA
A4GBAK0ayflJOPj0kRMxpw7vS+FO5+caMkt00LHtXULHGeTtmtwmiwwGTLQJ+b+x
W8vr/8gcfy7E6DsFlkGq52gTxaBjbhGRv3dIyx8leJLY661k4INesxIh5h6Op050
QMevL1VD7pSg6/jxJB0Oxo9ROb/EAsUHu2WAxrtBRadLy0n/MYICCTCCAgUCAQEw
ga4wgaAxCzAJBgNVBAYTAkRFMRUwEwYDVQQIEwxCcnRsaW4gU3RhdGUxDzANBgNV
BAcTBkJlcmxpbjETMBEGA1UEChMKWmVydGlmaWNvbjEMMAoGA1UECxMDUk5EMR0w
GwYDVQQDExRUaHVuZGVyYmlyZCBFeHRlcm5hbDEnMCUGCSqGSIb3DQEJARYYdGh1
bmRlcmJpcmRAZXh0ZXJuYWwuY29tAgkA6wuANug7V1AwCQYFKw4DAhoFAKCBsTAY
BgkqhkiG9w0BCQMxCwYJKoZIhvcNAQcBMBwGCSqGSIb3DQEJBTEPFw0wODAxMTcw
OTE2NDdaMCMGCSqGSIb3DQEJBDEWBBRzcl5uX8GSFcuVKZ3x4dgVNH6m7DBSBgkq
hkiG9w0BCQ8xRTBDMAoGCCqGSIb3DQMHMA4GCCqGSIb3DQMCAgIAgDANBggqhkiG
9w0DAgIBQDAHBgUrDgMCBzANBggqhkiG9w0DAgIBKDANBgkqhkiG9w0BAQEFAASB
gHLe2xcOWHtsSocQxvTcgTd8bznZUIwsu+2+K75/KRIBrEPg9tvPWNr9Af2jYrxt
AJCdLl8NSBXglszszkP7NnDoZMdBfZvNFr1I5L+41RDAGzAErw23Y3wtTt0aivpu
r9rBuuTEldZQa4BTaiGiBWl9rE7helkcoJPxmWXyAbmI

------1ABC9146925AEBE03F7FA2757971449C--


```

I could parse it manually in my own script but it can before I'd like to know whether or not there is already a script doing this.

Thanks,
Tex

---

