---
title: "Missing Authority Certificate formats for GeoTrust in Lubuntu variants"
date: 2016-06-19
forum: Security
---

### Post by nadrach on 2016-06-19
I use the ePub site [www.epubli.co.uk](www.epubli.co.uk) and have recently found issues with Firefox denying login access to the site because of an invalid security certificate, and I have to generate a security exception on each visit, private browsing deleting the exception on browser closure.
But not on every PC.
I have three active Lubuntu systems:
32-bit 14.04.1, installed 2 years ago, updated ever since;
64-bit 16.04, installed a few weeks ago, updated;
64-bit 14.04.4 installed as a reversion a week after trying 16.04 (doesn't work well with Alkinea), updated ever since.
I have problems with the first 2, but the last one is fine.
Currently have Firefox 47.0 on all three.
The issue traces to the list of authority certificate formats for GeoTrust Inc.
Three are missing from the 32-bit 14.04.1 and 64-bit 16.04 versions of Lubuntu (as shown in the certificate lists in Firefox).
The missing authority certificate formats (and dates of validity) are:
  RapidSSL SHA256 CA - G4   (30/06/15 - 30/06/25)
  GeoTrust SSL CA - G3         (05/11/13 - 29/05/22)
  RapidSSL SHA256 CA - G3   (29/08/14 - 20/05/22)

and it is a certificate of the last format that ePubli are using, which is valid until 2017.

Why are the certificate lists different between versions of the same OS?

---

