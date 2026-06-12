---
title: "Curse Client Installation Issues"
date: 2011-02-05
forum: Wine
---

### Post by stephanmir on 2011-02-05
Hi everyone,

This is my first time posting in the forums, so I apologise if this isn't the correct location to post. Also I am an absolute beginner at Ubuntu.

My issue is with Curse Client.

I've installed World of Warcraft and placed my addons in the interface / addons directory, but it is not showing in World of Warcraft (due to no addons button at the login screen). So I figured if I install Curse Client I would be able to have that automatically configure my addons to show up in game.

My problem is when installing Curse Client. I download the setup.exe from [www.curse.com]("http://www.curse.com") and placed it on my desktop. When I use Wine to install it, it is set up to run as Windows 2000 and I have installed IE6 with Winetricks.  The issue comes after I click the first accept button, it attempts to download a file called CurseClient and it automatically gives it a text document extension. 

This is what is contained in the file CurseClient:
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <assemblyIdentity name="CurseClient.application" version="4.0.1.104" publicKeyToken="eee711038731a406" language="neutral" processorArchitecture="msil" xmlns="urn:schemas-microsoft-com:asm.v1" />
  <description asmv2:publisher="Curse" asmv2:product="Curse Client" asmv2:supportUrl="http://clientsupport.curse.com/" co.v1:errorReportUrl="http://clientsupport.curse.com/" xmlns="urn:schemas-microsoft-com:asm.v1" />
  <deployment install="true" mapFileExtensions="true" minimumRequiredVersion="4.0.1.96" co.v1:createDesktopShortcut="true" />
  <dependency>
    <dependentAssembly dependencyType="install" codebase="Application Files\CurseClient_4_0_1_104\CurseClient.exe.manifest" size="32482">
      <assemblyIdentity name="CurseClient.exe" version="4.0.1.104" publicKeyToken="eee711038731a406" language="neutral" processorArchitecture="msil" type="win32" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>FzStapaDzneC4D8wADOsaeZMJlo=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=&quot;Curse, Inc.&quot;, OU=Digital ID Class 3 - Microsoft Software Validation v2, O=&quot;Curse, Inc.&quot;, L=San Francisco, S=California, C=US" issuerKeyHash="97d06ba82670c8a13f941f082dc4359ba4a11ef2" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#"><SignedInfo><CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" /><SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1" /><Reference URI=""><Transforms><Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature" /><Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" /></Transforms><DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" /><DigestValue>T372A/QMeQnCUWUjKus/fqVO/Kk=</DigestValue></Reference></SignedInfo><SignatureValue>AVUlMw+qy57IVvTU+ppYTCBtS2l2Z8j0Knl3wD2WKHp6OaG2zhdlbOJTYDHbLKY4pmXopSgN3EQ576JQhfJePMW2ffsj/ulyhB8dGgkCpUkmmfX7UJEqhpqQwSmJTfGZo+c4/5Kj9jHNN+rMMHEyP0Ffo4VENQkH+R5wMnvia74=</SignatureValue><KeyInfo Id="StrongNameKeyInfo"><KeyValue><RSAKeyValue><Modulus>kZU0bDRrlmyQR12zVEsA0ipTh/H6raSCwjT37VJIgMwybaYpAdLQ42Yn23tLwGbYyM624J1CU369mga9cMxBoAW2sBUbGdx48FMb6F2uFwBelG/l0kBjWgfNG7GCOVShUBwMNx8v8IYpC4gZw5IvUroc468WFPiigdyzMXxyis8=</Modulus><Exponent>AQAB</Exponent></RSAKeyValue></KeyValue><msrel:RelData xmlns:msrel="http://schemas.microsoft.com/windows/rel/2005/reldata"><r:license xmlns:r="urn:mpeg:mpeg21:2003:01-REL-R-NS" xmlns:as="http://schemas.microsoft.com/windows/pki/2005/Authenticode"><r:grant><as:ManifestInformation Hash="a9fc4ea57e3feb2a236551c209790cf403f67e4f" Description="" Url=""><as:assemblyIdentity name="CurseClient.application" version="4.0.1.104" publicKeyToken="eee711038731a406" language="neutral" processorArchitecture="msil" xmlns="urn:schemas-microsoft-com:asm.v1" /></as:ManifestInformation><as:SignedBy /><as:AuthenticodePublisher><as:X509SubjectName>CN="Curse, Inc.", OU=Digital ID Class 3 - Microsoft Software Validation v2, O="Curse, Inc.", L=San Francisco, S=California, C=US</as:X509SubjectName></as:AuthenticodePublisher></r:grant><r:issuer><Signature Id="AuthenticodeSignature" xmlns="http://www.w3.org/2000/09/xmldsig#"><SignedInfo><CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" /><SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1" /><Reference URI=""><Transforms><Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature" /><Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" /></Transforms><DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" /><DigestValue>0YqxBegbOBpdb94/aL+pVakoQ8A=</DigestValue></Reference></SignedInfo><SignatureValue>MBjVQTgPOOZrAULQFkwhx1rjNSkj7MIi1kfCvE590UvlmXJV9bK6OpeJa2Ha6EBRKSf6V4ZNtMm3lUu99KtjiF6ocvuai4yeqyOf5SnmHZnvPNP7gYfmcQTYM+Wqt8Iymt77oXlXWsMuI6W69wK0FPrk7wx93Yj+NX0l4RXxXH0=</SignatureValue><KeyInfo><KeyValue><RSAKeyValue><Modulus>kZU0bDRrlmyQR12zVEsA0ipTh/H6raSCwjT37VJIgMwybaYpAdLQ42Yn23tLwGbYyM624J1CU369mga9cMxBoAW2sBUbGdx48FMb6F2uFwBelG/l0kBjWgfNG7GCOVShUBwMNx8v8IYpC4gZw5IvUroc468WFPiigdyzMXxyis8=</Modulus><Exponent>AQAB</Exponent></RSAKeyValue></KeyValue><X509Data><X509Certificate>MIIE6TCCA9GgAwIBAgIQCwb3tC43eEUoevdmVZu42zANBgkqhkiG9w0BAQUFADCBtjELMAkGA1UEBhMCVVMxFzAVBgNVBAoTDlZlcmlTaWduLCBJbmMuMR8wHQYDVQQLExZWZXJpU2lnbiBUcnVzdCBOZXR3b3JrMTswOQYDVQQLEzJUZXJtcyBvZiB1c2UgYXQgaHR0cHM6Ly93d3cudmVyaXNpZ24uY29tL3JwYSAoYykwOTEwMC4GA1UEAxMnVmVyaVNpZ24gQ2xhc3MgMyBDb2RlIFNpZ25pbmcgMjAwOS0yIENBMB4XDTA5MDYzMDAwMDAwMFoXDTEyMDYyMzIzNTk1OVowgaYxCzAJBgNVBAYTAlVTMRMwEQYDVQQIEwpDYWxpZm9ybmlhMRYwFAYDVQQHEw1TYW4gRnJhbmNpc2NvMRQwEgYDVQQKFAtDdXJzZSwgSW5jLjE+MDwGA1UECxM1RGlnaXRhbCBJRCBDbGFzcyAzIC0gTWljcm9zb2Z0IFNvZnR3YXJlIFZhbGlkYXRpb24gdjIxFDASBgNVBAMUC0N1cnNlLCBJbmMuMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCRlTRsNGuWbJBHXbNUSwDSKlOH8fqtpILCNPftUkiAzDJtpikB0tDjZifbe0vAZtjIzrbgnUJTfr2aBr1wzEGgBbawFRsZ3HjwUxvoXa4XAF6Ub+XSQGNaB80bsYI5VKFQHAw3Hy/whikLiBnDki9SuhzjrxYU+KKB3LMxfHKKzwIDAQABo4IBgzCCAX8wCQYDVR0TBAIwADAOBgNVHQ8BAf8EBAMCB4AwRAYDVR0fBD0wOzA5oDegNYYzaHR0cDovL2NzYzMtMjAwOS0yLWNybC52ZXJpc2lnbi5jb20vQ1NDMy0yMDA5LTIuY3JsMEQGA1UdIAQ9MDswOQYLYIZIAYb4RQEHFwMwKjAoBggrBgEFBQcCARYcaHR0cHM6Ly93d3cudmVyaXNpZ24uY29tL3JwYTATBgNVHSUEDDAKBggrBgEFBQcDAzB1BggrBgEFBQcBAQRpMGcwJAYIKwYBBQUHMAGGGGh0dHA6Ly9vY3NwLnZlcmlzaWduLmNvbTA/BggrBgEFBQcwAoYzaHR0cDovL2NzYzMtMjAwOS0yLWFpYS52ZXJpc2lnbi5jb20vQ1NDMy0yMDA5LTIuY2VyMB8GA1UdIwQYMBaAFJfQa6gmcMihP5QfCC3ENZukoR7yMBEGCWCGSAGG+EIBAQQEAwIEEDAWBgorBgEEAYI3AgEbBAgwBgEBAAEB/zANBgkqhkiG9w0BAQUFAAOCAQEAqhmV8Y/d09/71w2R8f1OQvHM3PIfj+0O/Ck7ZhurMIHj4K7Gyx0UfNfO62G0yz8nrI7E6TTMD9Y7ROLIeFU9gGkYEFW88plRE0lxtzU5s7f0BGscWZiSYmugfLvMOmyyHFOIoMi1TVNA6VVQLKawkA3cTsawXZVWjQNRbIfbVIUS3UmY3s2+xRZ9rrF7efW5xYP0Ngr+Q8KyMUpCSFW64/qhlyje/eiW0xIK9Ct09pFIcjYQauHE492X8WQsLIfIxm8llLAFGb4K3rLJSNBD29B/b37aGOlAKfkMBLr8Aj1vR8cbjTNPuXEff0dXNuYlQ8HTV09IXpIcOo+mU48R1w==</X509Certificate><X509Certificate>MIIE/DCCBGWgAwIBAgIQZVIm4bIuGOFZDymFrCLnXDANBgkqhkiG9w0BAQUFADBfMQswCQYDVQQGEwJVUzEXMBUGA1UEChMOVmVyaVNpZ24sIEluYy4xNzA1BgNVBAsTLkNsYXNzIDMgUHVibGljIFByaW1hcnkgQ2VydGlmaWNhdGlvbiBBdXRob3JpdHkwHhcNMDkwNTIxMDAwMDAwWhcNMTkwNTIwMjM1OTU5WjCBtjELMAkGA1UEBhMCVVMxFzAVBgNVBAoTDlZlcmlTaWduLCBJbmMuMR8wHQYDVQQLExZWZXJpU2lnbiBUcnVzdCBOZXR3b3JrMTswOQYDVQQLEzJUZXJtcyBvZiB1c2UgYXQgaHR0cHM6Ly93d3cudmVyaXNpZ24uY29tL3JwYSAoYykwOTEwMC4GA1UEAxMnVmVyaVNpZ24gQ2xhc3MgMyBDb2RlIFNpZ25pbmcgMjAwOS0yIENBMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAvmcdtGCqEElvVhd8Zslehg3V8ayncYOOi4n4iASJFQa6LYQhleTRnFBM+9IivdrysjU7Ho/DCfv8Ey5av4l8PTslHvbzWHuc9AG1xgq4gM6+J3RhZydNauXsgWFYeaPgFxASFSew4U00fytHIES53mYkZorNT7ofxTjIVJDhcvYZZnVquUlozzh5DaowqNssYEie16oUAamD1ziRMDkTlgM6fEBUtq3gLxuD3KgRUj4Cs9cr/SG2p1yjDwupphBQDjQuTafOyV4l1Iy88258KbwBXfwxh1rVjIVnWIgZoL818OoroyHnkPaD5ajtYHhee2CD/VcLXUENY1Rg1kMh7wIDAQABo4IB2zCCAdcwEgYDVR0TAQH/BAgwBgEB/wIBADBwBgNVHSAEaTBnMGUGC2CGSAGG+EUBBxcDMFYwKAYIKwYBBQUHAgEWHGh0dHBzOi8vd3d3LnZlcmlzaWduLmNvbS9jcHMwKgYIKwYBBQUHAgIwHhocaHR0cHM6Ly93d3cudmVyaXNpZ24uY29tL3JwYTAOBgNVHQ8BAf8EBAMCAQYwbQYIKwYBBQUHAQwEYTBfoV2gWzBZMFcwVRYJaW1hZ2UvZ2lmMCEwHzAHBgUrDgMCGgQUj+XTGoasjY5rw8+AatRIGCx7GS4wJRYjaHR0cDovL2xvZ28udmVyaXNpZ24uY29tL3ZzbG9nby5naWYwHQYDVR0lBBYwFAYIKwYBBQUHAwIGCCsGAQUFBwMDMDQGCCsGAQUFBwEBBCgwJjAkBggrBgEFBQcwAYYYaHR0cDovL29jc3AudmVyaXNpZ24uY29tMDEGA1UdHwQqMCgwJqAkoCKGIGh0dHA6Ly9jcmwudmVyaXNpZ24uY29tL3BjYTMuY3JsMCkGA1UdEQQiMCCkHjAcMRowGAYDVQQDExFDbGFzczNDQTIwNDgtMS01NTAdBgNVHQ4EFgQUl9BrqCZwyKE/lB8ILcQ1m6ShHvIwDQYJKoZIhvcNAQEFBQADgYEAiwPA3ZTYQaJhabAVqHjHMMaQPH5C9yS25INzFwR/BBCcoeL6gS/rwMpE53LgULZVECCDbpaS5JpRarQ3MdylLeuMAMcdT+dNMrqF+E6++mdVZfBqvnrKZDgaEBB4RXYx84Z6Aw9gwrNdnfaLZnaCG1nhg+W9SaU4VuXeQXcOWA8=</X509Certificate></X509Data></KeyInfo><Object><as:Timestamp>MIIJcQYJKoZIhvcNAQcCoIIJYjCCCV4CAQExCzAJBgUrDgMCGgUAMIGRBgkqhkiG
9w0BBwGggYMEgYAwGNVBOA845msBQtAWTCHHWuM1KSPswiLWR8K8Tn3RS+WZclX1
sro6l4lrYdroQFEpJ/pXhk20ybeVS730q2OIXqhy+5qLjJ6rI5/lKeYdme880/uB
h+ZxBNgz5aq3wjKa3vuheVdawy4jpbr3ArQU+uTvDH3diP41fSXhFfFcfaCCB0Yw
ggN6MIICYqADAgECAhA4Jdf6+GGvnvSQ5ya11lrVMA0GCSqGSIb3DQEBBQUAMFMx
CzAJBgNVBAYTAlVTMRcwFQYDVQQKEw5WZXJpU2lnbiwgSW5jLjErMCkGA1UEAxMi
VmVyaVNpZ24gVGltZSBTdGFtcGluZyBTZXJ2aWNlcyBDQTAeFw0wNzA2MTUwMDAw
MDBaFw0xMjA2MTQyMzU5NTlaMFwxCzAJBgNVBAYTAlVTMRcwFQYDVQQKEw5WZXJp
U2lnbiwgSW5jLjE0MDIGA1UEAxMrVmVyaVNpZ24gVGltZSBTdGFtcGluZyBTZXJ2
aWNlcyBTaWduZXIgLSBHMjCBnzANBgkqhkiG9w0BAQEFAAOBjQAwgYkCgYEAxLXy
UhW8iIZgKRZKWy9LkWuHkfM1VFg16tE2XmJNUlE0ccJ7Zh2JyN0qxGoK9jfZmHSR
9pKusLV2lvGpSmNFRy5rC5JOSyuM7lhKi9QH5Bos+IKqWNnNQvMtwHXejavHjh2a
bEwIlR7e2+9n4XLCScKeYDzh4r4Wo2N4aRR7rS0CAwEAAaOBxDCBwTA0BggrBgEF
BQcBAQQoMCYwJAYIKwYBBQUHMAGGGGh0dHA6Ly9vY3NwLnZlcmlzaWduLmNvbTAM
BgNVHRMBAf8EAjAAMDMGA1UdHwQsMCowKKAmoCSGImh0dHA6Ly9jcmwudmVyaXNp
Z24uY29tL3Rzcy1jYS5jcmwwFgYDVR0lAQH/BAwwCgYIKwYBBQUHAwgwDgYDVR0P
AQH/BAQDAgbAMB4GA1UdEQQXMBWkEzARMQ8wDQYDVQQDEwZUU0ExLTIwDQYJKoZI
hvcNAQEFBQADggEBAFDFS8gkgN/kDSTC3hqxoQKhpoItDIMVgTcKgg4ssFoXYbXY
Bf6I2/GRkbNWGkCm65K+ODmwdTZ0OphP5De6mYnKlUIdsLnHoI1X4PrVZARCNU4B
0TOiF8hNqifH8uGGTAI4TYN4xvxT4OvgBofdpJaeXgyY4qW+v4KFw2Dh360o2Mel
S2Taxxtbvaw5CNU4IqEziy+Kmuu8ByE/REEJB7VlHCS8SNNEgOuhz8kCtBTPVMcW
o4Bc+Xk+XXJ9iBeeLEOiylPOfT32Kjq4T5QApW0Kg135XlP0GLNXD3DD+/WtlaAO
F97EFoBgyQ8rboYE8ev0eCfRBcXuNFteuUky8jMwggPEMIIDLaADAgECAhBHvxmV
341SRkP3221IDTGkMA0GCSqGSIb3DQEBBQUAMIGLMQswCQYDVQQGEwJaQTEVMBMG
A1UECBMMV2VzdGVybiBDYXBlMRQwEgYDVQQHEwtEdXJiYW52aWxsZTEPMA0GA1UE
ChMGVGhhd3RlMR0wGwYDVQQLExRUaGF3dGUgQ2VydGlmaWNhdGlvbjEfMB0GA1UE
AxMWVGhhd3RlIFRpbWVzdGFtcGluZyBDQTAeFw0wMzEyMDQwMDAwMDBaFw0xMzEy
MDMyMzU5NTlaMFMxCzAJBgNVBAYTAlVTMRcwFQYDVQQKEw5WZXJpU2lnbiwgSW5j
LjErMCkGA1UEAxMiVmVyaVNpZ24gVGltZSBTdGFtcGluZyBTZXJ2aWNlcyBDQTCC
ASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAKnKsqTMzSCvCn2JrId18LRO
8d/BD79nYb2jZBzau/nKM6uEMIlYfozba902ng+/0ex48nemfm88v5OvDbpo9GyU
yr1SLatIPfW21V1fGwKf+i9rHqT3o5qmGsgC4X9MUuMOYOxAHH65Dd4/x7Tfh71f
emoxLgOZgROoRyDOMXMNVy3NeDQzlRKZErneaC+q5uPCiowqw4shh2a9g1hXb3W/
PKomh13KEBU8n4TqVMEKbsT+xUrduQcRlyJ82z4n0R547J8xyfHmIhnbxLNHQ5oa
X6AekORe9e588X2rYgGP9U0L3tAiVqiVza6Idq7uug3z5E3ZoPtooK4UO7OHwbsC
AwEAAaOB2zCB2DA0BggrBgEFBQcBAQQoMCYwJAYIKwYBBQUHMAGGGGh0dHA6Ly9v
Y3NwLnZlcmlzaWduLmNvbTASBgNVHRMBAf8ECDAGAQH/AgEAMEEGA1UdHwQ6MDgw
NqA0oDKGMGh0dHA6Ly9jcmwudmVyaXNpZ24uY29tL1RoYXd0ZVRpbWVzdGFtcGlu
Z0NBLmNybDATBgNVHSUEDDAKBggrBgEFBQcDCDAOBgNVHQ8BAf8EBAMCAQYwJAYD
VR0RBB0wG6QZMBcxFTATBgNVBAMTDFRTQTIwNDgtMS01MzANBgkqhkiG9w0BAQUF
AAOBgQBKa/nqWMJEHDGJeZkrlr+CrAHWHEzNsIpYbt8IKaNeyMqTE+cEUg3vRycv
ADiw5MmTTprUImIV9z83IU9wMYDxiziHs+jolwD+z1WWTiTSqSdOeq63YUHzKs7n
ydle3bsrhT61nbXZ4Vf/vrTFfvXPDJ7wl/4r0ztSGxs4J/c/SjGCAWwwggFoAgEB
MGcwUzELMAkGA1UEBhMCVVMxFzAVBgNVBAoTDlZlcmlTaWduLCBJbmMuMSswKQYD
VQQDEyJWZXJpU2lnbiBUaW1lIFN0YW1waW5nIFNlcnZpY2VzIENBAhA4Jdf6+GGv
nvSQ5ya11lrVMAkGBSsOAwIaBQCgXTAYBgkqhkiG9w0BCQMxCwYJKoZIhvcNAQcB
MBwGCSqGSIb3DQEJBTEPFw0xMDExMjAxNjA5MjFaMCMGCSqGSIb3DQEJBDEWBBQd
o0EbA5FC2hq7/nRjOozp4CqHtDANBgkqhkiG9w0BAQEFAASBgHdc5L7XVJIHuyv0
T14M/WC3CeuafQ9kO5TZjpVuNT4JZ/l7CfvfiSAB16jJrNUWulRblloZYDaotxWM
HxXif1cr1czOq4j9fFwJ3J3W6Tm3R+0eSEKduhcATXPUaU9Gk+TIpoHUxDuUoDkJ
Kmy9dasFdCNACxEGmmVc+JtfkQKB
</as:Timestamp></Object></Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>






Ok, so sorry about all the spam it generated. What is this file? How do I run it? I attempted to rename with an executable extension (.exe) and use wine to load it, but I received an error.

BTW, I haven't found any recent updated pages on how to install CurseClient using Ubuntu version 10.10 with the newest Wine and newest CurseClient so I'm not sure if the old stuff they tell me to do still works.

Thanks for reading this, please let me know what I'm doing wrong.

Best Regards,

Stephan

---

### Post by stephanmir on 2011-02-06
bump

---

### Post by Tweak42 on 2011-02-08
I'm using the latest version of Wine (1.3.13) and Curse Client 3.0.0.10  I used winetricks to install ie8 and it works, but sometimes hangs at login and I need to kill it and relaunch.  It almost always works the 2nd try.

Make sure you are using 3.0 series installer because the 4.0 does NOT work.  The 3.0 download link is "Previous: v3 for Windows" under the 4.0 download.  Ignore any prompts asking you to upgrade to 4.0 or "newer version".

Heres the appDB entry:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22334](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22334)

Mine hasn't prompted to update to 3.0.0.11 yet, but since everything works I'm not going to mess with it.

---

