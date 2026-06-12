---
title: "CIS Benchmark Fail - Password Issues"
date: 2021-08-30
forum: Security
---

### Post by seeptiim on 2021-08-30
Hello! I have found that Ubuntu fails the following CIS Benchmarks:

3010 - Ensure retry option for passwords is less than 3
3011 - Ensure passwords are longer than 14 characters
3012 - Ensure passwords contain at least one digit
3013 - Ensure passwords contain at least one lowercase character
3014 - Ensure passwords contain at least one uppercase character
3015 - Ensure passwords contain at least one special character
3016 - Ensure lockout for failed password attempts is configured
3017 - Ensure password hashing algorithm is SHA-512
3018 - Ensure passwords in /etc/shadow are hashed with SHA-512 or SHA-256
3019 - Ensure password expiration is 365 days or less

All of these are related to password policy. Shouldn't these all be enforced by Ubuntu?

Thank you in advance!
[COLOR=#000000]Hello! I found that Ubuntu fails the following CIS Benchmarks:[/COLOR]

---

### Post by TheFu on 2021-08-30
> **seeptiim said:**
> Hello! I have found that Ubuntu fails the following CIS Benchmarks:

3010 - Ensure retry option for passwords is less than 3
3011 - Ensure passwords are longer than 14 characters
3012 - Ensure passwords contain at least one digit
3013 - Ensure passwords contain at least one lowercase character
3014 - Ensure passwords contain at least one uppercase character
3015 - Ensure passwords contain at least one special character
3016 - Ensure lockout for failed password attempts is configured
3017 - Ensure password hashing algorithm is SHA-512
3018 - Ensure passwords in /etc/shadow are hashed with SHA-512 or SHA-256
3019 - Ensure password expiration is 365 days or less

All of these are related to password policy. Shouldn't these all be enforced by Ubuntu? 

That is a matter of opinion. Feel free to change the settings on your system(s) if you like.
Blindly following someone else's recommendation or recommendations for govt security needs in a home environment is counter productive.  If you work under a contract that says "follow XYZ standards", they that is why you are being paid. Automating this group of items is trivial. Running any devops tool will modify the settings in under a 1 seconds.  Heck, a trivial sed script should do it too.  Every admin should know sed.

Did you look up the actual defaults under Ubuntu?  Which release? Defaults can change from release to release. Backwards compatibility is important for existing systems.

---

