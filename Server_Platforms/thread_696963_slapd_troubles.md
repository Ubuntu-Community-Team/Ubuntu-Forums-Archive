---
title: "slapd troubles"
date: 2008-02-14
forum: Server Platforms
---

### Post by moos3 on 2008-02-14
I'm running into a issue with the latest version of ubuntu server and slapd not liking access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword

I have followed the configuration howto and instructions to a T but its throwing a cow with that line. I go into debug mode and get the following output
```

root@edgecomb:/home/richard# slapd -d 16383
@(#) $OpenLDAP: slapd 2.3.35 (Dec  3 2007 20:02:39) $
	buildd@terranova:/build/buildd/openldap2.3-2.3.35/debian/build/servers/slapd
daemon_init: <null>
daemon_init: listen on ldap:///
daemon_init: 1 listeners to open...
ldap_url_parse_ext(ldap:///)
daemon: listener initialized ldap:///
daemon_init: 2 listeners opened
slapd init: initiated server.
slap_sasl_init: initialized!
reading config file /etc/ldap/slapd.conf
line 11 (include         /etc/ldap/schema/core.schema)
reading config file /etc/ldap/schema/core.schema
line 89 (attributetype ( 2.5.4.2 NAME 'knowledgeInformation' DESC 'RFC2256: knowledge information' EQUALITY caseIgnoreMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{32768} ))
line 98 (attributetype ( 2.5.4.4 NAME ( 'sn' 'surname' ) DESC 'RFC2256: last (family) name(s) for which the entity is known by' SUP name ))
line 104 (attributetype ( 2.5.4.5 NAME 'serialNumber' DESC 'RFC2256: serial number of the entity' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.44{64} ))
line 108 (attributetype ( 2.5.4.6 NAME ( 'c' 'countryName' ) DESC 'RFC2256: ISO-3166 country 2-letter code' SUP name SINGLE-VALUE ))
line 112 (attributetype ( 2.5.4.7 NAME ( 'l' 'localityName' ) DESC 'RFC2256: locality which this object resides in' SUP name ))
line 116 (attributetype ( 2.5.4.8 NAME ( 'st' 'stateOrProvinceName' ) DESC 'RFC2256: state or province which this object resides in' SUP name ))
line 122 (attributetype ( 2.5.4.9 NAME ( 'street' 'streetAddress' ) DESC 'RFC2256: street address of this object' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{128} ))
line 126 (attributetype ( 2.5.4.10 NAME ( 'o' 'organizationName' ) DESC 'RFC2256: organization this object belongs to' SUP name ))
line 130 (attributetype ( 2.5.4.11 NAME ( 'ou' 'organizationalUnitName' ) DESC 'RFC2256: organizational unit this object belongs to' SUP name ))
line 134 (attributetype ( 2.5.4.12 NAME 'title' DESC 'RFC2256: title associated with the entity' SUP name ))
line 146 (attributetype ( 2.5.4.14 NAME 'searchGuide' DESC 'RFC2256: search guide, deprecated by enhancedSearchGuide' SYNTAX 1.3.6.1.4.1.1466.115.121.1.25 ))
line 152 (attributetype ( 2.5.4.15 NAME 'businessCategory' DESC 'RFC2256: business category' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{128} ))
line 158 (attributetype ( 2.5.4.16 NAME 'postalAddress' DESC 'RFC2256: postal address' EQUALITY caseIgnoreListMatch SUBSTR caseIgnoreListSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.41 ))
line 164 (attributetype ( 2.5.4.17 NAME 'postalCode' DESC 'RFC2256: postal code' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{40} ))
line 170 (attributetype ( 2.5.4.18 NAME 'postOfficeBox' DESC 'RFC2256: Post Office Box' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{40} ))
line 176 (attributetype ( 2.5.4.19 NAME 'physicalDeliveryOfficeName' DESC 'RFC2256: Physical Delivery Office Name' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{128} ))
line 182 (attributetype ( 2.5.4.20 NAME 'telephoneNumber' DESC 'RFC2256: Telephone Number' EQUALITY telephoneNumberMatch SUBSTR telephoneNumberSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.50{32} ))
line 186 (attributetype ( 2.5.4.21 NAME 'telexNumber' DESC 'RFC2256: Telex Number' SYNTAX 1.3.6.1.4.1.1466.115.121.1.52 ))
line 190 (attributetype ( 2.5.4.22 NAME 'teletexTerminalIdentifier' DESC 'RFC2256: Teletex Terminal Identifier' SYNTAX 1.3.6.1.4.1.1466.115.121.1.51 ))
line 194 (attributetype ( 2.5.4.23 NAME ( 'facsimileTelephoneNumber' 'fax' ) DESC 'RFC2256: Facsimile (Fax) Telephone Number' SYNTAX 1.3.6.1.4.1.1466.115.121.1.22 ))
line 200 (attributetype ( 2.5.4.24 NAME 'x121Address' DESC 'RFC2256: X.121 Address' EQUALITY numericStringMatch SUBSTR numericStringSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.36{15} ))
line 206 (attributetype ( 2.5.4.25 NAME 'internationaliSDNNumber' DESC 'RFC2256: international ISDN number' EQUALITY numericStringMatch SUBSTR numericStringSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.36{16} ))
line 211 (attributetype ( 2.5.4.26 NAME 'registeredAddress' DESC 'RFC2256: registered postal address' SUP postalAddress SYNTAX 1.3.6.1.4.1.1466.115.121.1.41 ))
line 217 (attributetype ( 2.5.4.27 NAME 'destinationIndicator' DESC 'RFC2256: destination indicator' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.44{128} ))
line 222 (attributetype ( 2.5.4.28 NAME 'preferredDeliveryMethod' DESC 'RFC2256: preferred delivery method' SYNTAX 1.3.6.1.4.1.1466.115.121.1.14 SINGLE-VALUE ))
line 228 (attributetype ( 2.5.4.29 NAME 'presentationAddress' DESC 'RFC2256: presentation address' EQUALITY presentationAddressMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.43 SINGLE-VALUE ))
line 233 (attributetype ( 2.5.4.30 NAME 'supportedApplicationContext' DESC 'RFC2256: supported application context' EQUALITY objectIdentifierMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.38 ))
line 237 (attributetype ( 2.5.4.31 NAME 'member' DESC 'RFC2256: member of a group' SUP distinguishedName ))
line 241 (attributetype ( 2.5.4.32 NAME 'owner' DESC 'RFC2256: owner (of the object)' SUP distinguishedName ))
line 245 (attributetype ( 2.5.4.33 NAME 'roleOccupant' DESC 'RFC2256: occupant of role' SUP distinguishedName ))
line 263 (attributetype ( 2.5.4.36 NAME 'userCertificate' DESC 'RFC2256: X.509 user certificate, use ;binary' EQUALITY certificateExactMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.8 ))
line 270 (attributetype ( 2.5.4.37 NAME 'cACertificate' DESC 'RFC2256: X.509 CA certificate, use ;binary' EQUALITY certificateExactMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.8 ))
line 275 (attributetype ( 2.5.4.38 NAME 'authorityRevocationList' DESC 'RFC2256: X.509 authority revocation list, use ;binary' SYNTAX 1.3.6.1.4.1.1466.115.121.1.9 ))
line 280 (attributetype ( 2.5.4.39 NAME 'certificateRevocationList' DESC 'RFC2256: X.509 certificate revocation list, use ;binary' SYNTAX 1.3.6.1.4.1.1466.115.121.1.9 ))
line 285 (attributetype ( 2.5.4.40 NAME 'crossCertificatePair' DESC 'RFC2256: X.509 cross certificate pair, use ;binary' SYNTAX 1.3.6.1.4.1.1466.115.121.1.10 ))
line 295 (attributetype ( 2.5.4.42 NAME ( 'givenName' 'gn' ) DESC 'RFC2256: first name(s) for which the entity is known by' SUP name ))
line 299 (attributetype ( 2.5.4.43 NAME 'initials' DESC 'RFC2256: initials of some or all of names, but not the surname(s).' SUP name ))
line 303 (attributetype ( 2.5.4.44 NAME 'generationQualifier' DESC 'RFC2256: name qualifier indicating a generation' SUP name ))
line 308 (attributetype ( 2.5.4.45 NAME 'x500UniqueIdentifier' DESC 'RFC2256: X.500 unique identifier' EQUALITY bitStringMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.6 ))
line 315 (attributetype ( 2.5.4.46 NAME 'dnQualifier' DESC 'RFC2256: DN qualifier' EQUALITY caseIgnoreMatch ORDERING caseIgnoreOrderingMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.44 ))
line 319 (attributetype ( 2.5.4.47 NAME 'enhancedSearchGuide' DESC 'RFC2256: enhanced search guide' SYNTAX 1.3.6.1.4.1.1466.115.121.1.21 ))
line 324 (attributetype ( 2.5.4.48 NAME 'protocolInformation' DESC 'RFC2256: protocol information' EQUALITY protocolInformationMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.42 ))
line 334 (attributetype ( 2.5.4.50 NAME 'uniqueMember' DESC 'RFC2256: unique member of a group' EQUALITY uniqueMemberMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.34 ))
line 340 (attributetype ( 2.5.4.51 NAME 'houseIdentifier' DESC 'RFC2256: house identifier' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{32768} ))
line 345 (attributetype ( 2.5.4.52 NAME 'supportedAlgorithms' DESC 'RFC2256: supported algorithms' SYNTAX 1.3.6.1.4.1.1466.115.121.1.49 ))
line 350 (attributetype ( 2.5.4.53 NAME 'deltaRevocationList' DESC 'RFC2256: delta revocation list; use ;binary' SYNTAX 1.3.6.1.4.1.1466.115.121.1.9 ))
line 354 (attributetype ( 2.5.4.54 NAME 'dmdName' DESC 'RFC2256: name of DMD' SUP name ))
line 358 (attributetype ( 2.5.4.65 NAME 'pseudonym' DESC 'X.520(4th): pseudonym for the object' SUP name ))
line 378 (objectclass ( 2.5.6.2 NAME 'country' DESC 'RFC2256: a country' SUP top STRUCTURAL MUST c MAY ( searchGuide $ description ) ))
line 383 (objectclass ( 2.5.6.3 NAME 'locality' DESC 'RFC2256: a locality' SUP top STRUCTURAL MAY ( street $ seeAlso $ searchGuide $ st $ l $ description ) ))
line 394 (objectclass ( 2.5.6.4 NAME 'organization' DESC 'RFC2256: an organization' SUP top STRUCTURAL MUST o MAY ( userPassword $ searchGuide $ seeAlso $ businessCategory $ 	x121Address $ registeredAddress $ destinationIndicator $ 	preferredDeliveryMethod $ telexNumber $ teletexTerminalIdentifier $ 	telephoneNumber $ internationaliSDNNumber $  	facsimileTelephoneNumber $ street $ postOfficeBox $ postalCode $ 	postalAddress $ physicalDeliveryOfficeName $ st $ l $ description ) ))
line 405 (objectclass ( 2.5.6.5 NAME 'organizationalUnit' DESC 'RFC2256: an organizational unit' SUP top STRUCTURAL MUST ou MAY ( userPassword $ searchGuide $ seeAlso $ businessCategory $ 	x121Address $ registeredAddress $ destinationIndicator $ 	preferredDeliveryMethod $ telexNumber $ teletexTerminalIdentifier $ 	telephoneNumber $ internationaliSDNNumber $ 	facsimileTelephoneNumber $ street $ postOfficeBox $ postalCode $ 	postalAddress $ physicalDeliveryOfficeName $ st $ l $ description ) ))
line 411 (objectclass ( 2.5.6.6 NAME 'person' DESC 'RFC2256: a person' SUP top STRUCTURAL MUST ( sn $ cn ) MAY ( userPassword $ telephoneNumber $ seeAlso $ description ) ))
line 420 (objectclass ( 2.5.6.7 NAME 'organizationalPerson' DESC 'RFC2256: an organizational person' SUP person STRUCTURAL MAY ( title $ x121Address $ registeredAddress $ destinationIndicator $ 	preferredDeliveryMethod $ telexNumber $ teletexTerminalIdentifier $ 	telephoneNumber $ internationaliSDNNumber $  	facsimileTelephoneNumber $ street $ postOfficeBox $ postalCode $ 	postalAddress $ physicalDeliveryOfficeName $ ou $ st $ l ) ))
line 431 (objectclass ( 2.5.6.8 NAME 'organizationalRole' DESC 'RFC2256: an organizational role' SUP top STRUCTURAL MUST cn MAY ( x121Address $ registeredAddress $ destinationIndicator $ 	preferredDeliveryMethod $ telexNumber $ teletexTerminalIdentifier $ 	telephoneNumber $ internationaliSDNNumber $ facsimileTelephoneNumber $ 	seeAlso $ roleOccupant $ preferredDeliveryMethod $ street $ 	postOfficeBox $ postalCode $ postalAddress $ 	physicalDeliveryOfficeName $ ou $ st $ l $ description ) ))
line 437 (objectclass ( 2.5.6.9 NAME 'groupOfNames' DESC 'RFC2256: a group of names (DNs)' SUP top STRUCTURAL MUST ( member $ cn ) MAY ( businessCategory $ seeAlso $ owner $ ou $ o $ description ) ))
line 448 (objectclass ( 2.5.6.10 NAME 'residentialPerson' DESC 'RFC2256: an residential person' SUP person STRUCTURAL MUST l MAY ( businessCategory $ x121Address $ registeredAddress $ 	destinationIndicator $ preferredDeliveryMethod $ telexNumber $ 	teletexTerminalIdentifier $ telephoneNumber $ internationaliSDNNumber $ 	facsimileTelephoneNumber $ preferredDeliveryMethod $ street $ 	postOfficeBox $ postalCode $ postalAddress $ 	physicalDeliveryOfficeName $ st $ l ) ))
line 454 (objectclass ( 2.5.6.11 NAME 'applicationProcess' DESC 'RFC2256: an application process' SUP top STRUCTURAL MUST cn MAY ( seeAlso $ ou $ l $ description ) ))
line 461 (objectclass ( 2.5.6.12 NAME 'applicationEntity' DESC 'RFC2256: an application entity' SUP top STRUCTURAL MUST ( presentationAddress $ cn ) MAY ( supportedApplicationContext $ seeAlso $ ou $ o $ l $ description ) ))
line 466 (objectclass ( 2.5.6.13 NAME 'dSA' DESC 'RFC2256: a directory system agent (a server)' SUP applicationEntity STRUCTURAL MAY knowledgeInformation ))
line 472 (objectclass ( 2.5.6.14 NAME 'device' DESC 'RFC2256: a device' SUP top STRUCTURAL MUST cn MAY ( serialNumber $ seeAlso $ owner $ ou $ o $ l $ description ) ))
line 477 (objectclass ( 2.5.6.15 NAME 'strongAuthenticationUser' DESC 'RFC2256: a strong authentication user' SUP top AUXILIARY MUST userCertificate ))
line 483 (objectclass ( 2.5.6.16 NAME 'certificationAuthority' DESC 'RFC2256: a certificate authority' SUP top AUXILIARY MUST ( authorityRevocationList $ certificateRevocationList $ 	cACertificate ) MAY crossCertificatePair ))
line 489 (objectclass ( 2.5.6.17 NAME 'groupOfUniqueNames' DESC 'RFC2256: a group of unique names (DN and Unique Identifier)' SUP top STRUCTURAL MUST ( uniqueMember $ cn ) MAY ( businessCategory $ seeAlso $ owner $ ou $ o $ description ) ))
line 494 (objectclass ( 2.5.6.18 NAME 'userSecurityInformation' DESC 'RFC2256: a user security information' SUP top AUXILIARY MAY ( supportedAlgorithms ) ))
line 498 (objectclass ( 2.5.6.16.2 NAME 'certificationAuthority-V2' SUP certificationAuthority AUXILIARY MAY ( deltaRevocationList ) ))
line 504 (objectclass ( 2.5.6.19 NAME 'cRLDistributionPoint' SUP top STRUCTURAL MUST ( cn ) MAY ( certificateRevocationList $ authorityRevocationList $ 	deltaRevocationList ) ))
line 514 (objectclass ( 2.5.6.20 NAME 'dmd' SUP top STRUCTURAL MUST ( dmdName ) MAY ( userPassword $ searchGuide $ seeAlso $ businessCategory $ 	x121Address $ registeredAddress $ destinationIndicator $preferredDeliveryMethod $ telexNumber $ teletexTerminalIdentifier $ 	telephoneNumber $ internationaliSDNNumber $ facsimileTelephoneNumber $ 	street $ postOfficeBox $ postalCode $ postalAddress $ 	physicalDeliveryOfficeName $ st $ l $ description ) ))
line 522 (objectclass ( 2.5.6.21 NAME 'pkiUser' DESC 'RFC2587: a PKI user' SUP top AUXILIARY MAY userCertificate ))
line 528 (objectclass ( 2.5.6.22 NAME 'pkiCA' DESC 'RFC2587: PKI certificate authority' SUP top AUXILIARY MAY ( authorityRevocationList $ certificateRevocationList $ 	cACertificate $ crossCertificatePair ) ))
line 533 (objectclass ( 2.5.6.23 NAME 'deltaCRL' DESC 'RFC2587: PKI user' SUP top AUXILIARY MAY deltaRevocationList ))
line 546 (objectclass ( 1.3.6.1.4.1.250.3.15 NAME 'labeledURIObject' DESC 'RFC2079: object that contains the URI attribute type' SUP top AUXILIARY MAY ( labeledURI ) ))
line 563 (attributetype ( 0.9.2342.19200300.100.1.3 NAME ( 'mail' 'rfc822Mailbox' ) DESC 'RFC1274: RFC822 Mailbox'    EQUALITY caseIgnoreIA5Match    SUBSTR caseIgnoreIA5SubstringsMatch    SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} ))
line 568 (objectclass ( 0.9.2342.19200300.100.4.19 NAME 'simpleSecurityObject' DESC 'RFC1274: simple security object' SUP top AUXILIARY MUST userPassword ))
line 576 (attributetype ( 0.9.2342.19200300.100.1.25 NAME ( 'dc' 'domainComponent' ) DESC 'RFC1274/2247: domain component' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE ))
line 581 (objectclass ( 1.3.6.1.4.1.1466.344 NAME 'dcObject' DESC 'RFC2247: domain component object' SUP top AUXILIARY MUST dc ))
line 586 (objectclass ( 1.3.6.1.1.3.1 NAME 'uidObject' DESC 'RFC2377: uid object' SUP top AUXILIARY MUST uid ))
line 594 (attributetype ( 0.9.2342.19200300.100.1.37 NAME 'associatedDomain' DESC 'RFC1274: domain associated with object' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 602 (attributetype ( 1.2.840.113549.1.9.1 NAME ( 'email' 'emailAddress' 'pkcs9email' ) DESC 'RFC3280: legacy attribute for email addresses in DNs' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{128} ))
line 12 (include         /etc/ldap/schema/cosine.schema)
reading config file /etc/ldap/schema/cosine.schema
line 49 (attributetype ( 0.9.2342.19200300.100.1.2 NAME 'textEncodedORAddress' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 61 (attributetype ( 0.9.2342.19200300.100.1.4 NAME 'info' DESC 'RFC1274: general information' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{2048} ))
line 68 (attributetype ( 0.9.2342.19200300.100.1.5 NAME ( 'drink' 'favouriteDrink' ) DESC 'RFC1274: favorite drink' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 74 (attributetype ( 0.9.2342.19200300.100.1.6 NAME 'roomNumber' DESC 'RFC1274: room number' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 78 (attributetype ( 0.9.2342.19200300.100.1.7 NAME 'photo' DESC 'RFC1274: photo (G3 fax)' SYNTAX 1.3.6.1.4.1.1466.115.121.1.23{25000} ))
line 84 (attributetype ( 0.9.2342.19200300.100.1.8 NAME 'userClass' DESC 'RFC1274: category of user' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 90 (attributetype ( 0.9.2342.19200300.100.1.9 NAME 'host' DESC 'RFC1274: host computer' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 95 (attributetype ( 0.9.2342.19200300.100.1.10 NAME 'manager' DESC 'RFC1274: DN of manager' EQUALITY distinguishedNameMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 ))
line 101 (attributetype ( 0.9.2342.19200300.100.1.11 NAME 'documentIdentifier' DESC 'RFC1274: unique identifier of document' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 107 (attributetype ( 0.9.2342.19200300.100.1.12 NAME 'documentTitle' DESC 'RFC1274: title of document' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 113 (attributetype ( 0.9.2342.19200300.100.1.13 NAME 'documentVersion' DESC 'RFC1274: version of document' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 118 (attributetype ( 0.9.2342.19200300.100.1.14 NAME 'documentAuthor' DESC 'RFC1274: DN of author of document' EQUALITY distinguishedNameMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 ))
line 124 (attributetype ( 0.9.2342.19200300.100.1.15 NAME 'documentLocation' DESC 'RFC1274: location of document original' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 131 (attributetype ( 0.9.2342.19200300.100.1.20 NAME ( 'homePhone' 'homeTelephoneNumber' ) DESC 'RFC1274: home telephone number' EQUALITY telephoneNumberMatch SUBSTR telephoneNumberSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.50 ))
line 136 (attributetype ( 0.9.2342.19200300.100.1.21 NAME 'secretary' DESC 'RFC1274: DN of secretary' EQUALITY distinguishedNameMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 ))
line 139 (attributetype ( 0.9.2342.19200300.100.1.22 NAME 'otherMailbox' SYNTAX 1.3.6.1.4.1.1466.115.121.1.39 ))
line 165 (attributetype ( 0.9.2342.19200300.100.1.26 NAME 'aRecord' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 171 (attributetype ( 0.9.2342.19200300.100.1.27 NAME 'mDRecord' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 176 (attributetype ( 0.9.2342.19200300.100.1.28 NAME 'mXRecord' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 181 (attributetype ( 0.9.2342.19200300.100.1.29 NAME 'nSRecord' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 186 (attributetype ( 0.9.2342.19200300.100.1.30 NAME 'sOARecord' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 191 (attributetype ( 0.9.2342.19200300.100.1.31 NAME 'cNAMERecord' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 201 (attributetype ( 0.9.2342.19200300.100.1.38 NAME 'associatedName' DESC 'RFC1274: DN of entry associated with domain' EQUALITY distinguishedNameMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 ))
line 207 (attributetype ( 0.9.2342.19200300.100.1.39 NAME 'homePostalAddress' DESC 'RFC1274: home postal address' EQUALITY caseIgnoreListMatch SUBSTR caseIgnoreListSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.41 ))
line 213 (attributetype ( 0.9.2342.19200300.100.1.40 NAME 'personalTitle' DESC 'RFC1274: personal title' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 220 (attributetype ( 0.9.2342.19200300.100.1.41 NAME ( 'mobile' 'mobileTelephoneNumber' ) DESC 'RFC1274: mobile telephone number' EQUALITY telephoneNumberMatch SUBSTR telephoneNumberSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.50 ))
line 227 (attributetype ( 0.9.2342.19200300.100.1.42 NAME ( 'pager' 'pagerTelephoneNumber' ) DESC 'RFC1274: pager telephone number' EQUALITY telephoneNumberMatch SUBSTR telephoneNumberSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.50 ))
line 234 (attributetype ( 0.9.2342.19200300.100.1.43 NAME ( 'co' 'friendlyCountryName' ) DESC 'RFC1274: friendly country name' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 ))
line 239 (attributetype ( 0.9.2342.19200300.100.1.44 NAME 'uniqueIdentifier' DESC 'RFC1274: unique identifer' EQUALITY caseIgnoreMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 245 (attributetype ( 0.9.2342.19200300.100.1.45 NAME 'organizationalStatus' DESC 'RFC1274: organizational status' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 251 (attributetype ( 0.9.2342.19200300.100.1.46 NAME 'janetMailbox' DESC 'RFC1274: Janet mailbox' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} ))
line 256 (attributetype ( 0.9.2342.19200300.100.1.47 NAME 'mailPreferenceOption' DESC 'RFC1274: mail preference option' SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 ))
line 262 (attributetype ( 0.9.2342.19200300.100.1.48 NAME 'buildingName' DESC 'RFC1274: name of building' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15{256} ))
line 266 (attributetype ( 0.9.2342.19200300.100.1.49 NAME 'dSAQuality' DESC 'RFC1274: DSA Quality' SYNTAX 1.3.6.1.4.1.1466.115.121.1.19 SINGLE-VALUE ))
line 270 (attributetype ( 0.9.2342.19200300.100.1.50 NAME 'singleLevelQuality' DESC 'RFC1274: Single Level Quality' SYNTAX 1.3.6.1.4.1.1466.115.121.1.13 SINGLE-VALUE ))
line 274 (attributetype ( 0.9.2342.19200300.100.1.51 NAME 'subtreeMinimumQuality' DESC 'RFC1274: Subtree Mininum Quality' SYNTAX 1.3.6.1.4.1.1466.115.121.1.13 SINGLE-VALUE ))
line 278 (attributetype ( 0.9.2342.19200300.100.1.52 NAME 'subtreeMaximumQuality' DESC 'RFC1274: Subtree Maximun Quality' SYNTAX 1.3.6.1.4.1.1466.115.121.1.13 SINGLE-VALUE ))
line 282 (attributetype ( 0.9.2342.19200300.100.1.53 NAME 'personalSignature' DESC 'RFC1274: Personal Signature (G3 fax)' SYNTAX 1.3.6.1.4.1.1466.115.121.1.23 ))
line 287 (attributetype ( 0.9.2342.19200300.100.1.54 NAME 'dITRedirect' DESC 'RFC1274: DIT Redirect' EQUALITY distinguishedNameMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 ))
line 291 (attributetype ( 0.9.2342.19200300.100.1.55 NAME 'audio' DESC 'RFC1274: audio (u-law)' SYNTAX 1.3.6.1.4.1.1466.115.121.1.4{25000} ))
line 297 (attributetype ( 0.9.2342.19200300.100.1.56 NAME 'documentPublisher' DESC 'RFC1274: publisher of document' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 ))
line 316 (objectclass ( 0.9.2342.19200300.100.4.4 NAME ( 'pilotPerson' 'newPilotPerson' ) SUP person STRUCTURAL MAY ( userid $ textEncodedORAddress $ rfc822Mailbox $ 	favouriteDrink $ roomNumber $ userClass $ 	homeTelephoneNumber $ homePostalAddress $ secretary $ 	personalTitle $ preferredDeliveryMethod $ businessCategory $ 	janetMailbox $ otherMailbox $ mobileTelephoneNumber $ 	pagerTelephoneNumber $ organizationalStatus $ 	mailPreferenceOption $ personalSignature ) ))
line 323 (objectclass ( 0.9.2342.19200300.100.4.5 NAME 'account' SUP top STRUCTURAL MUST userid MAY ( description $ seeAlso $ localityName $ 	organizationName $ organizationalUnitName $ host ) ))
line 332 (objectclass ( 0.9.2342.19200300.100.4.6 NAME 'document' SUP top STRUCTURAL MUST documentIdentifier MAY ( commonName $ description $ seeAlso $ localityName $ 	organizationName $ organizationalUnitName $ 	documentTitle $ documentVersion $ documentAuthor $ 	documentLocation $ documentPublisher ) ))
line 338 (objectclass ( 0.9.2342.19200300.100.4.7 NAME 'room' SUP top STRUCTURAL MUST commonName MAY ( roomNumber $ description $ seeAlso $ telephoneNumber ) ))
line 345 (objectclass ( 0.9.2342.19200300.100.4.9 NAME 'documentSeries' SUP top STRUCTURAL MUST commonName MAY ( description $ seeAlso $ telephonenumber $ 	localityName $ organizationName $ organizationalUnitName ) ))
line 359 (objectclass ( 0.9.2342.19200300.100.4.13 NAME 'domain' SUP top STRUCTURAL MUST domainComponent MAY ( associatedName $ organizationName $ description $ 	businessCategory $ seeAlso $ searchGuide $ userPassword $ 	localityName $ stateOrProvinceName $ streetAddress $ 	physicalDeliveryOfficeName $ postalAddress $ postalCode $ 	postOfficeBox $ streetAddress $ 	facsimileTelephoneNumber $ internationalISDNNumber $ 	telephoneNumber $ teletexTerminalIdentifier $ telexNumber $ 	preferredDeliveryMethod $ destinationIndicator $ 	registeredAddress $ x121Address ) ))
line 370 (objectclass ( 0.9.2342.19200300.100.4.14 NAME 'RFC822localPart' SUP domain STRUCTURAL MAY ( commonName $ surname $ description $ seeAlso $ telephoneNumber $ 	physicalDeliveryOfficeName $ postalAddress $ postalCode $ 	postOfficeBox $ streetAddress $ 	facsimileTelephoneNumber $ internationalISDNNumber $ 	telephoneNumber $ teletexTerminalIdentifier $ 	telexNumber $ preferredDeliveryMethod $ destinationIndicator $ 	registeredAddress $ x121Address ) ))
line 376 (objectclass ( 0.9.2342.19200300.100.4.15 NAME 'dNSDomain' SUP domain STRUCTURAL MAY ( ARecord $ MDRecord $ MXRecord $ NSRecord $ 	SOARecord $ CNAMERecord ) ))
line 381 (objectclass ( 0.9.2342.19200300.100.4.17 NAME 'domainRelatedObject' DESC 'RFC1274: an object related to an domain' SUP top AUXILIARY MUST associatedDomain ))
line 385 (objectclass ( 0.9.2342.19200300.100.4.18 NAME 'friendlyCountry' SUP country STRUCTURAL MUST friendlyCountryName ))
line 394 (objectclass ( 0.9.2342.19200300.100.4.20 NAME 'pilotOrganization' SUP ( organization $ organizationalUnit ) STRUCTURAL MAY buildingName ))
line 398 (objectclass ( 0.9.2342.19200300.100.4.21 NAME 'pilotDSA' SUP dsa STRUCTURAL MAY dSAQuality ))
line 404 (objectclass ( 0.9.2342.19200300.100.4.22 NAME 'qualityLabelledData' SUP top AUXILIARY MUST dsaQuality MAY ( subtreeMinimumQuality $ subtreeMaximumQuality ) ))
line 13 (include         /etc/ldap/schema/nis.schema)
reading config file /etc/ldap/schema/nis.schema
line 53 (attributetype ( 1.3.6.1.1.1.1.2 NAME 'gecos' DESC 'The GECOS field; the common name' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE ))
line 58 (attributetype ( 1.3.6.1.1.1.1.3 NAME 'homeDirectory' DESC 'The absolute path to the home directory' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE ))
line 63 (attributetype ( 1.3.6.1.1.1.1.4 NAME 'loginShell' DESC 'The path to the login shell' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE ))
line 67 (attributetype ( 1.3.6.1.1.1.1.5 NAME 'shadowLastChange' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 71 (attributetype ( 1.3.6.1.1.1.1.6 NAME 'shadowMin' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 75 (attributetype ( 1.3.6.1.1.1.1.7 NAME 'shadowMax' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 79 (attributetype ( 1.3.6.1.1.1.1.8 NAME 'shadowWarning' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 83 (attributetype ( 1.3.6.1.1.1.1.9 NAME 'shadowInactive' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 87 (attributetype ( 1.3.6.1.1.1.1.10 NAME 'shadowExpire' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 91 (attributetype ( 1.3.6.1.1.1.1.11 NAME 'shadowFlag' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 96 (attributetype ( 1.3.6.1.1.1.1.12 NAME 'memberUid' EQUALITY caseExactIA5Match SUBSTR caseExactIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 101 (attributetype ( 1.3.6.1.1.1.1.13 NAME 'memberNisNetgroup' EQUALITY caseExactIA5Match SUBSTR caseExactIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 105 (attributetype ( 1.3.6.1.1.1.1.14 NAME 'nisNetgroupTriple' DESC 'Netgroup triple' SYNTAX 1.3.6.1.1.1.0.0 ))
line 109 (attributetype ( 1.3.6.1.1.1.1.15 NAME 'ipServicePort' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 112 (attributetype ( 1.3.6.1.1.1.1.16 NAME 'ipServiceProtocol' SUP name ))
line 116 (attributetype ( 1.3.6.1.1.1.1.17 NAME 'ipProtocolNumber' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 120 (attributetype ( 1.3.6.1.1.1.1.18 NAME 'oncRpcNumber' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE ))
line 125 (attributetype ( 1.3.6.1.1.1.1.19 NAME 'ipHostNumber' DESC 'IP address' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{128} ))
line 130 (attributetype ( 1.3.6.1.1.1.1.20 NAME 'ipNetworkNumber' DESC 'IP network' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{128} SINGLE-VALUE ))
line 135 (attributetype ( 1.3.6.1.1.1.1.21 NAME 'ipNetmaskNumber' DESC 'IP netmask' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{128} SINGLE-VALUE ))
line 140 (attributetype ( 1.3.6.1.1.1.1.22 NAME 'macAddress' DESC 'MAC address' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{128} ))
line 144 (attributetype ( 1.3.6.1.1.1.1.23 NAME 'bootParameter' DESC 'rpc.bootparamd parameter' SYNTAX 1.3.6.1.1.1.0.1 ))
line 149 (attributetype ( 1.3.6.1.1.1.1.24 NAME 'bootFile' DESC 'Boot image name' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 152 (attributetype ( 1.3.6.1.1.1.1.26 NAME 'nisMapName' SUP name ))
line 157 (attributetype ( 1.3.6.1.1.1.1.27 NAME 'nisMapEntry' EQUALITY caseExactIA5Match SUBSTR caseExactIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{1024} SINGLE-VALUE ))
line 165 (objectclass ( 1.3.6.1.1.1.2.0 NAME 'posixAccount' DESC 'Abstraction of an account with POSIX attributes' SUP top AUXILIARY MUST ( cn $ uid $ uidNumber $ gidNumber $ homeDirectory ) MAY ( userPassword $ loginShell $ gecos $ description ) ))
line 173 (objectclass ( 1.3.6.1.1.1.2.1 NAME 'shadowAccount' DESC 'Additional attributes for shadow passwords' SUP top AUXILIARY MUST uid MAY ( userPassword $ shadowLastChange $ shadowMin $       shadowMax $ shadowWarning $ shadowInactive $       shadowExpire $ shadowFlag $ description ) ))
line 179 (objectclass ( 1.3.6.1.1.1.2.2 NAME 'posixGroup' DESC 'Abstraction of a group of accounts' SUP top STRUCTURAL MUST ( cn $ gidNumber ) MAY ( userPassword $ memberUid $ description ) ))
line 185 (objectclass ( 1.3.6.1.1.1.2.3 NAME 'ipService' DESC 'Abstraction an Internet Protocol service' SUP top STRUCTURAL MUST ( cn $ ipServicePort $ ipServiceProtocol ) MAY ( description ) ))
line 191 (objectclass ( 1.3.6.1.1.1.2.4 NAME 'ipProtocol' DESC 'Abstraction of an IP protocol' SUP top STRUCTURAL MUST ( cn $ ipProtocolNumber $ description ) MAY description ))
line 197 (objectclass ( 1.3.6.1.1.1.2.5 NAME 'oncRpc' DESC 'Abstraction of an ONC/RPC binding' SUP top STRUCTURAL MUST ( cn $ oncRpcNumber $ description ) MAY description ))
line 203 (objectclass ( 1.3.6.1.1.1.2.6 NAME 'ipHost' DESC 'Abstraction of a host, an IP device' SUP top AUXILIARY MUST ( cn $ ipHostNumber ) MAY ( l $ description $ manager ) ))
line 209 (objectclass ( 1.3.6.1.1.1.2.7 NAME 'ipNetwork' DESC 'Abstraction of an IP network' SUP top STRUCTURAL MUST ( cn $ ipNetworkNumber ) MAY ( ipNetmaskNumber $ l $ description $ manager ) ))
line 215 (objectclass ( 1.3.6.1.1.1.2.8 NAME 'nisNetgroup' DESC 'Abstraction of a netgroup' SUP top STRUCTURAL MUST cn MAY ( nisNetgroupTriple $ memberNisNetgroup $ description ) ))
line 221 (objectclass ( 1.3.6.1.1.1.2.9 NAME 'nisMap' DESC 'A generic abstraction of a NIS map' SUP top STRUCTURAL MUST nisMapName MAY description ))
line 227 (objectclass ( 1.3.6.1.1.1.2.10 NAME 'nisObject' DESC 'An entry in a NIS map' SUP top STRUCTURAL MUST ( cn $ nisMapEntry $ nisMapName ) MAY description ))
line 232 (objectclass ( 1.3.6.1.1.1.2.11 NAME 'ieee802Device' DESC 'A device with a MAC address' SUP top AUXILIARY MAY macAddress ))
line 237 (objectclass ( 1.3.6.1.1.1.2.12 NAME 'bootableDevice' DESC 'A device with boot parameters' SUP top AUXILIARY MAY ( bootFile $ bootParameter ) ))
line 14 (include         /etc/ldap/schema/inetorgperson.schema)
reading config file /etc/ldap/schema/inetorgperson.schema
line 36 (attributetype ( 2.16.840.1.113730.3.1.1 NAME 'carLicense' DESC 'RFC2798: vehicle license or registration plate' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 ))
line 46 (attributetype ( 2.16.840.1.113730.3.1.2 NAME 'departmentNumber' DESC 'RFC2798: identifies a department within an organization' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 ))
line 59 (attributetype ( 2.16.840.1.113730.3.1.241 NAME 'displayName' DESC 'RFC2798: preferred name to be used when displaying entries' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 SINGLE-VALUE ))
line 70 (attributetype ( 2.16.840.1.113730.3.1.3 NAME 'employeeNumber' DESC 'RFC2798: numerically identifies an employee within an organization' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 SINGLE-VALUE ))
line 81 (attributetype ( 2.16.840.1.113730.3.1.4 NAME 'employeeType' DESC 'RFC2798: type of employment for a person' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 ))
line 92 (attributetype ( 0.9.2342.19200300.100.1.60 NAME 'jpegPhoto' DESC 'RFC2798: a JPEG image' SYNTAX 1.3.6.1.4.1.1466.115.121.1.28 ))
line 107 (attributetype ( 2.16.840.1.113730.3.1.39 NAME 'preferredLanguage' DESC 'RFC2798: preferred written or spoken language for a person' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 SINGLE-VALUE ))
line 123 (attributetype ( 2.16.840.1.113730.3.1.40 NAME 'userSMIMECertificate' DESC 'RFC2798: PKCS#7 SignedData used to support S/MIME' SYNTAX 1.3.6.1.4.1.1466.115.121.1.5 ))
line 135 (attributetype ( 2.16.840.1.113730.3.1.216 NAME 'userPKCS12' DESC 'RFC2798: personal identity information, a PKCS #12 PFX' SYNTAX 1.3.6.1.4.1.1466.115.121.1.5 ))
line 155 (objectclass	( 2.16.840.1.113730.3.2.2    NAME 'inetOrgPerson' DESC 'RFC2798: Internet Organizational Person'    SUP organizationalPerson    STRUCTURAL MAY ( 	audio $ businessCategory $ carLicense $ departmentNumber $ 	displayName $ employeeNumber $ employeeType $ givenName $ 	homePhone $ homePostalAddress $ initials $ jpegPhoto $ 	labeledURI $ mail $ manager $ mobile $ o $ pager $ 	photo $ roomNumber $ secretary $ uid $ userCertificate $ 	x500uniqueIdentifier $ preferredLanguage $ 	userSMIMECertificate $ userPKCS12 ) ))
line 15 (incldue		/etc/ldap/schema/samba.schema)
/etc/ldap/slapd.conf: line 15: unknown directive <incldue> inside backend database definition (ignored).
line 16 (include		/etc/ldap/schema/misc.schema)
reading config file /etc/ldap/schema/misc.schema
line 31 (attributetype ( 2.16.840.1.113730.3.1.13 NAME 'mailLocalAddress' DESC 'RFC822 email address of this recipient' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} ))
line 38 (attributetype ( 2.16.840.1.113730.3.1.18 NAME 'mailHost' DESC 'FQDN of the SMTP/MTA of this recipient' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} SINGLE-VALUE ))
line 45 (attributetype ( 2.16.840.1.113730.3.1.47 NAME 'mailRoutingAddress' DESC 'RFC822 routing address of this recipient' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26{256} SINGLE-VALUE ))
line 54 (objectclass ( 2.16.840.1.113730.3.2.147 NAME 'inetLocalMailRecipient' DESC 'Internet local mail recipient' SUP top AUXILIARY MAY	( mailLocalAddress $ mailHost $ mailRoutingAddress ) ))
line 64 (attributetype ( 1.3.6.1.4.1.42.2.27.2.1.15 NAME 'rfc822MailMember' DESC 'rfc822 mail address of group member(s)' EQUALITY caseIgnoreIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 ))
line 75 (objectclass ( 1.3.6.1.4.1.42.2.27.1.2.5 NAME 'nisMailAlias' DESC 'NIS mail alias' SUP top STRUCTURAL MUST cn MAY rfc822MailMember ))
line 20 (pidfile         /var/run/slapd/slapd.pid)
line 23 (argsfile        /var/run/slapd/slapd.args)
line 26 (loglevel        0)
line 29 (modulepath	/usr/lib/ldap)
line 30 (moduleload	back_bdb)
loaded module back_bdb
bdb_back_initialize: initialize BDB backend
bdb_back_initialize: Sleepycat Software: Berkeley DB 4.2.52: (December  3, 2003)
module back_bdb: null module registered
line 33 (sizelimit 500)
line 37 (tool-threads 1)
line 43 (backend		bdb)
line 44 (checkpoint 512 30)
/etc/ldap/slapd.conf: line 44: unknown directive <checkpoint> inside backend database definition (ignored).
line 56 (database        bdb)
bdb_db_init: Initializing BDB database
line 59 (suffix          "dc=moos3,dc=com")
>>> dnPrettyNormal: <dc=moos3,dc=com>
=> ldap_bv2dn(dc=moos3,dc=com,0)
<= ldap_bv2dn(dc=moos3,dc=com)=0 
=> ldap_dn2bv(272)
<= ldap_dn2bv(dc=moos3,dc=com)=0 
=> ldap_dn2bv(272)
<= ldap_dn2bv(dc=moos3,dc=com)=0 
<<< dnPrettyNormal: <dc=moos3,dc=com>, <dc=moos3,dc=com>
line 66 (directory       "/var/lib/ldap")
line 70 (dbconfig set_cachesize 0 2097152 0)
line 77 (dbconfig set_lk_max_objects 1500)
line 79 (dbconfig set_lk_max_locks 1500)
line 81 (dbconfig set_lk_max_lockers 1500)
line 84 (index           objectClass eq)
index objectClass 0x0004
line 87 (lastmod         on)
line 101 (access to attrs=userPassword,sambaNTPassword,sambaLMPassword        by dn="cn=admin,dc=moos3,dc=com" write        by anonymous auth        by self write        by * none)
/etc/ldap/slapd.conf: line 101: unknown attr "sambaNTPassword" in to clause
<access clause> ::= access to <what> [ by <who> [ <access> ] [ <control> ] ]+ 
<what> ::= * | dn[.<dnstyle>=<DN>] [filter=<filter>] [attrs=<attrspec>]
<attrspec> ::= <attrname> [val[/<matchingRule>][.<attrstyle>]=<value>] | <attrlist>
<attrlist> ::= <attr> [ , <attrlist> ]
<attr> ::= <attrname> | @<objectClass> | !<objectClass> | entry | children
<who> ::= [ * | anonymous | users | self | dn[.<dnstyle>]=<DN> ]
	[ realanonymous | realusers | realself | realdn[.<dnstyle>]=<DN> ]
	[dnattr=<attrname>]
	[realdnattr=<attrname>]
	[group[/<objectclass>[/<attrname>]][.<style>]=<group>]
	[peername[.<peernamestyle>]=<peer>] [sockname[.<style>]=<name>]
	[domain[.<domainstyle>]=<domain>] [sockurl[.<style>]=<url>]
	[aci[=<attrname>]]
	[ssf=<n>] [transport_ssf=<n>] [tls_ssf=<n>] [sasl_ssf=<n>]
<style> ::= exact | regex | base(Object)
<dnstyle> ::= base(Object) | one(level) | sub(tree) | children | exact | regex
<attrstyle> ::= exact | regex | base(Object) | one(level) | sub(tree) | children
<peernamestyle> ::= exact | regex | ip | path
<domainstyle> ::= exact | regex | base(Object) | sub(tree)
<access> ::= [[real]self]{<level>|<priv>}
<level> ::= none|disclose|auth|compare|search|read|{write|add|delete}|manage
<priv> ::= {=|+|-}{0|d|x|c|s|r|{w|a|z}|m}+
<control> ::= [ stop | continue | break ]

/etc/ldap/slapd.conf: line 101: <access> handler exited with 1!
slapd destroy: freeing system resources.
slapd stopped.
connections_destroy: nothing to destroy.

```

Ideas on why?

---

### Post by moos3 on 2008-02-14
my slapd.conf file
```

# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
incldue		/etc/ldap/schema/samba.schema
include		/etc/ldap/schema/misc.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

# Where the dynamically loaded modules are stored
modulepath	/usr/lib/ldap
moduleload	back_bdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend		bdb
checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend		<other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=moos3,dc=com"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
# rootdn          "cn=admin,dc=moos3,dc=com"

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057
# for more information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile	/var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
# access to attrs=userPassword,shadowLastChange
access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
        by dn="cn=admin,dc=moos3,dc=com" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work 
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=moos3,dc=com" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=moos3,dc=com" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix		"dc=debian,dc=org"

```

---

### Post by astrotech226 on 2008-02-14
I think I found your problem.  The last error makes me think you don't have samba.schema installed.  So looking closer at your config:

```
# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
incldue		/etc/ldap/schema/samba.schema
include		/etc/ldap/schema/misc.schema
```

The word "Include" is mispelled.  Fix that and see what happens.

---

### Post by moos3 on 2008-02-15
how are you spelling include? I dont think a "I" in clude is going to make a difference consider the original file inlcude is all lower case. I did check the files they are there and just for **** and giggles I chmod 777 all of them and nothing. Ideas?

---

### Post by astrotech226 on 2008-02-15
Look very closely at the line for samba.schema.  It is spelled "incldue".  So slapd is  passing over this line and not including the samba portion.  You have attributes that need the samba part and that's why the service is failing.

I'm pretty sure that if you change the line to start with "include", it will work fine.

---

