---
title: "performance degradation with our .NET 6 LTS applications after upgrading from Ubuntu"
date: 2024-10-07
forum: Server Platforms
---

### Post by virajauthnex on 2024-10-07
[COLOR=#000000][FONT=Verdana]We’re experiencing significant performance degradation with our .NET 6 LTS applications after upgrading from Ubuntu 20.04 to Ubuntu 24.04. Despite performing various performance tune-ups and ensuring that the hardware and resource allocations are identical, we've observed no improvements. We suspect that this slowdown might be related to changes in the new kernel.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]To analyze the issue, we developed a simple tool using .NET that performs tasks like signing data with a self-signed certificate (SHA-256), reading app configuration files, chain builds, and converting private keys to objects. Across the board, these operations are noticeably slower on Ubuntu 24.04 compared to 20.04.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Our applications performed well on Ubuntu 20.04S, but with its EOL approaching, we're compelled to migrate to 24.04, however the performance hit has been a major roadblock for us and we are unable to proceed with the migration due to this issue.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Has anyone else encountered similar issues, or can anyone provide insight on what might be causing this slowdown in Ubuntu 24.04?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The below screenshot describes the slowness with the time.[/FONT][/COLOR]
[https://authnex-my.sharepoint.com/:i...xSZmg?e=jjmhh1]("https://authnex-my.sharepoint.com/:i:/p/viraj/EcfK_W6IscxOgSEJCWA13JwB0epn6DTmja7RxLEoHxSZmg?e=jjmhh1")

[LIST]
[*]We used same performance vms to demonstrate this issue.
[*]We performed some tune-ups like enabling swap/ disabling swap.
[*]Disabled Apparmor
[*]Downgraded Openssl to the same version of Ubuntu 20.04 has, etc.
[*]Using same Signed Certificates that we used in Ubuntu 20.04
[/LIST]

---

