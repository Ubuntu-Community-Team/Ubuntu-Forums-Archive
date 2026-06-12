---
title: "websites that validate email addresses"
date: 2020-03-08
forum: The Cafe
---

### Post by Skaperen on 2020-03-08
i have heard there are websites that "validate" email addresses by other than RFC standards.  in particular i am concerned with those that reject addresses that have . or + or - (or any combination other than a run of 2 or more periods).  do *you* run a website that rejects email address that are technically valid according to the RFC standards for any purpose other than email hosting?  i am wanting to find out why.  i am curious if it is an incompetent decision maker, or unwarranted paranoia, or if a genuine issue has been discovered.

---

### Post by TheFu on 2020-03-09
I've had an email address rejected by a huge big-box retailer before.  They didn't like one of the words in the address I used with them. It was not offensive.  I was able to create the account using it, but never able to login again using it. The validations between the creation and login were coded differently. ;(

Thanks for the idea to use ..... in my email addresses going forward.  Anything I can do to make life harder for spammers is a good thing.  It isn't like I'll ever have to type the address myself, anywhere.  As long as an email address begins with an alpha character, pretty much anything should be legal.  I need to try _the+++fu....waz##99@domain.com_ for fun.

Why would someone not allow that sort of email?  Because they don't know or care.  The regex to match 99% of all email addresses is fairly short. [https://www.regular-expressions.info/email.html](https://www.regular-expressions.info/email.html)

The regex to match all allowed, legal, email address possible, is about a page long. Simple. Laziness or a lack of regex mastery.
[https://emailregex.com/](https://emailregex.com/)

Most places simply don't want to waste the time.

---

### Post by SeijiSensei on 2020-03-09
I suspect many providers are pretty clueless about the variety of legitimate email addresses there can be. 

I limit my checking to the domain part (valid name? has an MX? accepts mail directly on port 25?).

[php]
       function check_email($address) {

                # return code indicates result
                # 0 = email ok
                # 1 = bad address form
                # 2 = no mx record for domain
                # 3 = no mx record and host doesn't accept smtp

                $bademail=0;

                # no @
                if (!strstr($address,"@")) {
                        $bademail=1;

                } else if (strstr($address,",")) { 
                        $bademail=1;

                } else {
                        $emailchk=explode("@",$address);
                        $mailname=trim($emailchk[0]);
                        $maildom=trim($emailchk[1]);

                        # check domain part for invalid characters
                        if (preg_match("/[^a-zA-Z0-9\.\-]/",$maildom)) {
                                $bademail=1;
                        }

                        # check domain part has a valid mx record
                        if (!$bademail) {
                                # note: host returns a null string to sysout if no record found
                                # and it reports "host not found" to syserr
                                $mxchk=`host -t mx $maildom`;
                                if (empty($mxchk) || strstr($mxchk,"NXDOMAIN")) {
                                        $bademail=2;

                                        # check if host itself receives mail per RFC2821
                                        $nmapchk=`nmap -P0 -PT25 -sT -p 25 $maildom | grep smtp | grep open`;
                                        if (!empty($nmapchk)) {
                                                $bademail=0;
                                        } else {
                                                $bademail=3;
                                        }
                                }
                        }

                }

                return $bademail;

        }

[/php]

---

### Post by Skaperen on 2020-03-09
so, for initial form checking, before you do any network traffic, you don't check the LHS at all?  that's where i've been finding bad rejects.  so, apparently, many clueless decision makers are doing that.

i say "decision makers" as i don't want to blame programmers and sysadmins if the boss is the real trouble maker.

---

### Post by TheFu on 2020-03-09
> **Skaperen said:**
> so, for initial form checking, before you do any network traffic, you don't check the LHS at all?  that's where i've been finding bad rejects.  so, apparently, many clueless decision makers are doing that.

i say "decision makers" as i don't want to blame programmers and sysadmins if the boss is the real trouble maker.

I've never seen any requirements or boss care about email addresses enough to be involved to that level.  Almost always, it is the guy doing the implementation going with a "good enough" answer.  Many validation function expect there to be an '@' which isn't strictly required.  bang paths are still valid.

---

### Post by Skaperen on 2020-03-09
a business intent on reselling addresses to spammers might decide to disallow registration with tagged email addresses.  their programmer might need the paycheck.

---

### Post by TheFu on 2020-03-10
I use someone elses well-tested code:

```
use Email::Valid;
my $address = Email::Valid->address('dog@heaven.org');
print ($address ? 'yes' : 'no');
```

Or
```
use Data::Validate::Email qw(is_email is_email_rfc822);
my $v = Data::Validate::Email->new();
die "not an email" unless ($v->is_email_rfc822('cat@heaven.org'));
```

DRY - no need to reinvent this stuff.

---

### Post by Skaperen on 2020-03-10
has anyone soon Python or C versions of such code?

---

### Post by TheFu on 2020-03-11
Google C-snippets.
Google python email validation.  I've seen the python modules in the last 2 days.  The C stuff, probably 25 yrs ago.  Dr.Dobbs used to run all sorts of C example solutions for that stuff.

And there's always the RosettaCode site.

---

### Post by Skaperen on 2020-03-11
i guess there needs to be code ready for every possible system websites could be running out there.  i know someone who is still using OS/2 (but doesn't do user logins).

---

