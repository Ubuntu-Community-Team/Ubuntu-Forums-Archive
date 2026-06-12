---
title: "Strange Outbound Connection to 141.101.117.91 - curl"
date: 2013-03-28
forum: Security
---

### Post by Elludium_Q-36 on 2013-03-28
My machine had been idle and noticed net traffic.  Firestarter showed a connection to 141.101.117.91 with curl as the service or program.

From the description of package "curl":
> curl is a client to get files from servers using any of the supported
protocols. The command is designed to work without user interaction
or any kind of interactivity.

Yeah, no!  I don't mind the update notifier, but what is this?

Whois for 141.101.117.91 comes back as:
> #
# Query terms are ambiguous.  The query is assumed to be:
#     "n 141.101.117.91"
#
# Use "?" to get help.
#

#
# The following results may also be obtained via:
# [http://whois.arin.net/rest/nets;q=141.101.117.91?showDetails=true&showARIN=false&ext=netref2](http://whois.arin.net/rest/nets;q=141.101.117.91?showDetails=true&showARIN=false&ext=netref2)
#

NetRange:       141.0.0.0 - 141.255.255.255
CIDR:           141.0.0.0/8
OriginAS:       
NetName:        RIPE-ERX-141
NetHandle:      NET-141-0-0-0-0
Parent:         
NetType:        Early Registrations, Maintained by RIPE NCC
Comment:        These addresses have been further assigned to users in
Comment:        the RIPE NCC region.  Contact information can be found in
Comment:        the RIPE database at [http://www.ripe.net/whois](http://www.ripe.net/whois)
RegDate:        1993-05-01
Updated:        2009-05-18
Ref:            [http://whois.arin.net/rest/net/NET-141-0-0-0-0](http://whois.arin.net/rest/net/NET-141-0-0-0-0)

OrgName:        RIPE Network Coordination Centre
OrgId:          RIPE
Address:        P.O. Box 10096
City:           Amsterdam
StateProv:      
PostalCode:     1001EB
Country:        NL
RegDate:        
Updated:        2011-09-24
Ref:            [http://whois.arin.net/rest/org/RIPE](http://whois.arin.net/rest/org/RIPE)

ReferralServer: whois://whois.ripe.net:43

OrgTechHandle: RNO29-ARIN
OrgTechName:   RIPE NCC Operations
OrgTechPhone:  +31 20 535 4444 
OrgTechEmail:  [email]hostmaster@ripe.net[/email]
OrgTechRef:    [http://whois.arin.net/rest/poc/RNO29-ARIN](http://whois.arin.net/rest/poc/RNO29-ARIN)

OrgAbuseHandle: RNO29-ARIN
OrgAbuseName:   RIPE NCC Operations
OrgAbusePhone:  +31 20 535 4444 
OrgAbuseEmail:  [email]hostmaster@ripe.net[/email]
OrgAbuseRef:    [http://whois.arin.net/rest/poc/RNO29-ARIN](http://whois.arin.net/rest/poc/RNO29-ARIN)

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: [https://www.arin.net/whois_tou.html](https://www.arin.net/whois_tou.html)
#



Found a referral to whois.ripe.net:43.

% This is the RIPE Database query service.
% The objects are in RPSL format.
%
% The RIPE Database is subject to Terms and Conditions.
% See [http://www.ripe.net/db/support/db-terms-conditions.pdf](http://www.ripe.net/db/support/db-terms-conditions.pdf)

% Note: this output has been filtered.
%       To receive output for a database update, use the "-B" flag.

% Information related to '141.101.112.0 - 141.101.119.255'

inetnum:        141.101.112.0 - 141.101.119.255
netname:        CLOUDFLARE-EU
descr:          CloudFlare CDN network
country:        EU
admin-c:        CAC80-RIPE
tech-c:         CTC6-RIPE
status:         ASSIGNED PA
mnt-by:         MNT-CLOUDFLARE
mnt-lower:      MNT-CLOUDFLARE
mnt-routes:     MNT-CLOUDFLARE
source:         RIPE # Filtered

person:         CloudFlare Administrative Contact
address:        665 3rd Street, Suite 207 San Francisco CA 94107 US
phone:          +1-650-319-8930
nic-hdl:        CAC80-RIPE
abuse-mailbox:  [email]abuse@cloudflare.com[/email]
mnt-by:         MNT-CLOUDFLARE
source:         RIPE # Filtered

person:         CloudFlare Technical Contact
address:        665 3rd Street, Suite 207 San Francisco CA 94107 US
phone:          +1 (650) 319-8930
nic-hdl:        CTC6-RIPE
abuse-mailbox:  [email]abuse@cloudflare.com[/email]
mnt-by:         MNT-CLOUDFLARE
source:         RIPE # Filtered

% This query was served by the RIPE Database Query Service version 1.58.1 (WHOIS3)

For now, I added a firewall to block outbound, CIDR: 141.101.112.0/21

---

