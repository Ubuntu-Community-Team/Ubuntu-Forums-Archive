---
title: "Checking fiber port statistics on Ubuntu 22 with Hyper-V NPIV"
date: 2022-07-03
forum: Server Platforms
---

### Post by ardiver86 on 2022-07-03
We are running Ubuntu 22.04 on Hyper-V which has a couple fiber channel ports added utilizing NPIV. The ports show up in Ubuntu and I'm able to talk to the SAN but we are experience very degregated speeds and latency. I wanted to check the fiber port speeds to verify they are indeed each 8Gbps but I cannot for the life of me figure out how. I think this is because there isn't a PCIe fiber card attached so it must be attached these fiber ports to Ubuntu some other way?

Does anyone know how to get the fiber port data (specially the speed) in this type of scenario? LSPCI does not give me any data. Trying to do a "[COLOR=#000000][FONT=monospace]cat /sys/class/fc_host/host*/speed" doesn't work either because "speed" doesn't exist.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2022-07-04
It all depends on your implementation of NPIV and the HBA Fiber Channel Cards... You talk about two different animals. There is am implementation of NPIV for SANS, and then for VM network switches. Then from what end of that you want to check the speed and throughput... Which one is through MS Server or at least your Hyper-V host. Then the other is through the individual VM Guests. It's only going to be what piece of what your slowest piece of the path is going to be... 

For example, I use fiber backbones for backups and internal data retrieval, within my own domain. Then bonded connections for greater external throughput. I have been contracted by other companies, on bonded connections to their customers for cloud backups, to their own private cloud servers, for use 'Backups As A Service'. (One, of many, as an example. Linux or VMware solutions.) 

For you... You mention VM(s), as in Network speeds... Then mention Sans. There are tuned solutions for each.

Since you are 'here', and talking about how to get the throughput and speed of a network connection of your Ubuntu LTS 22.04 Server, (knowing it is not certified as LTS until July, with the release of patched 22.04.1)... I would suggest using this article for a jumping off point: [https://phoenixnap.com/kb/linux-network-speed-test](https://phoenixnap.com/kb/linux-network-speed-test). With Linux, there are so many choices. It all depends on what you want to do and use. (and what the specific requirements are.)

Personally, for my own, I use 'speedtest-cli', and 'traceroute' for external connections, and 'iperf' for monitoring and auditing throughput between my own (personal or contracted) connections that I have some type of control of. Then I use them in my own scripts, to present the tailored reports I want to present, and track. 

Depending on what you want to see, and the type of information you want to see and track, will guide you in what you end up using.

*** You imply that you have more than one HBA Fiber channel on that specific VM Host... And the  way you implied that, directed the level of skills I answered this  question to the target audience. Others might not understand this  answer.

EDIT: Just understand that that would only be one virtual connection of the shared Fiber HBA device. More virtual connections on that same shared device may affect the throughput. It goes the same logic as SR-IOV devices, as it relates to effective shared virtual throughput.

---

### Post by ardiver86 on 2022-07-04
I am referring to NPIV for SAN. I was unaware of the use case for ethernet in the virtualizated world. 

I have two 8Gbps HBA/SAN fiber cards in the hyperv host with NPIV enabled. I have added two fiber ports to the Ubuntu 22 guest OS so it would have two paths to the SAN for storage instead of using a virtual disk (vhdx)

What I have found is performance of using VHDX is much greater than using the fiber channel pass-through which is surprising. My theory is Ubuntu is not negotiating the correct speed on each port which is why it is much slower. The default multipathing config picks up the two paths and i condigured the partition and volume on /dev/mapper/mpatha*

Many articles refer to using lspci to look a fiber stuff but these commands do not give me much. I want to see the speed Ubuntu thinks it is but I cannot figure out how. How do I look at the speed it negotiated at in Ubuntu?

---

### Post by MAFoElffen on 2022-07-06
> **ardiver86 said:**
> I am referring to NPIV for SAN. I was unaware of the use case for ethernet in the virtualizated world. 

I have two 8Gbps HBA/SAN fiber cards in the hyperv host with NPIV enabled. I have added two fiber ports to the Ubuntu 22 guest OS so it would have two paths to the SAN for storage instead of using a virtual disk (vhdx)

What I have found is performance of [COLOR=#ff0000]using VHDX is much greater[/COLOR] than using the fiber channel pass-through which is surprising. My theory is Ubuntu is not negotiating the correct speed on each port which is why it is much slower. The default multipathing config picks up the two paths and [COLOR=#ff0000]i condigured the partition and volume on /dev/mapper/mpatha*[/COLOR]

[COLOR=#ff8c00]Many articles refer to using lspci to look a fiber stuff[/COLOR] but these commands do not give me much. I want to see the speed Ubuntu thinks it is but I cannot figure out how. How do I look at the speed it negotiated at in Ubuntu?
'lspci' is "not going to work for you", because you are using a Linux Server VM, on a Windows OS Hyper-V Host, which you are not passing through the HBA cards directly to the VM. 

IMHO, That is the right way to do that... Using NPIV to virtually share the HBA cards.

But what that does, and why 'lspci' is not longerr the tool tolook at your HBA cards, is that the Sever Guest is running within that Virtual Machine, and only see hoes that VM is configured as a machine (the virtual connections of NPIV sharedwith that VM).

If it where passed through,to a VM, or on metal, on a Linux Virtual Host, hosting the VM, then I would use a Bash script, using something like this: (This is a function from my Ama-Gi Project, that could slip into the 'system-info' script I wrote for UbuntForums.)
```

function GetFiberChannel() {
    # Based on this information: 
    echo -e "---------- Fiber Channel Controller Information From 'lspci'"
    cntrllr_busid_list=$(lspci | grep --color=never -i -e 'Fiber Channel ' \
        awk '{print $1}')

    if [ ! -z "$cntrllr_busid_list" ]
    then
        # Parse through list (array) and show detailed information on each
        for controller in ${cntrllr_busid_list}
        do
            sudo lspci -s $controller -vv
            echo ""
        done
    else
        echo -e "No fiber channel controller card found.
        echo ""
    fi
}

```
## ...and you parse through the output of that, and find other related  information located in directories '/sys/class/fc_host/host*/' to parse  through the 'port_name', 'node_name', 'speed', 'port_state',  'port_type', and 'statistics' files to get that specific information...  But since you since your VM Guest is shielded virtually from that  hardware...


From the guest, you could check read/write speeds of your SAN (end-to-end, or SAN to VM Guest)... The effective speed, point to point.

Since the Virtual Host is Windows (Server) Based, hosting the Linux Server, it can see the Fiber Channel Card directly, while you guest is shielded from it. In what you explained, I would be using a Powershell script on your Virtual Host (where the Fiber Channel Cards are physically installed), where your VM Server Guest is hosted on (Hyper-V service), and using 'Get-InitiatorPort and GetWmiObject to retrieve the information you want... Drilling through WMI, what I would concentrate on would be something like:
```

function Get-HBAInfo {
   [CmdletBinding()]
   Param
   (
     [Parameter(Mandatory=$false, ValueFromPipeline=$true, Position=0)]
     $ComputerName
   )

   Begin 
   {
      $Namespace = "root\WMI"
   } Process {
     $port = Get-WmiObject -Class MSFC_FibrePortHBAAttributes -Namespace $Namespace @PSBoundParameters
     $hbas = Get-WmiObject -Class MSFC_FCAdapterHBAAttributes -Namespace $Namespace @PSBoundParameters
     $hbaProp = $hbas | Get-Member -MemberType Property, AliasProperty | Select -ExpandProperty name | ? {$_ -notlike "__*"}
     $hbas = $hbas | Select $hbaProp
     $hbas | %{ $_.NodeWWN = ((($_.NodeWWN) | % {"{0:x2}" -f $_}) -join ":").ToUpper() }
 
     ForEach($hba in $hbas) {
       Add-Member -MemberType NoteProperty -InputObject $hba -Name FabricName -Value (
        ($port |? { $_.instancename -eq $hba.instancename}).attributes | `
        Select `
        @{Name='Fabric Name';Expression={(($_.fabricname | % {"{0:x2}" -f $_}) -join ":").ToUpper()}}, `
        @{Name='Port WWN';Expression={(($_.PortWWN | % {"{0:x2}" -f $_}) -join ":").ToUpper()}} 
        ) -passThru
    }
  }
}
Get-HBAInfo $env:COMPUTERNAME
```
Then use the Powershell CLI to get the other object names that you want to display...

Is that a clear enough "hint" to guide you in a direction to find out what you want? There is a simpler way...

Of course, since you are a Windows Server Sys Admin, you could just look at it manually though a GUI, by opening the "Storage Explorer" of Windows Server, where you can see both sides of the connection, where you can  see detailed information about the Fibre  Channel host bus adapters (HBAs) on your server, or on other servers in  your storage area network (SAN). It will show:

  
[LIST]
[*] The name of the server where the HBA is installed 
[*] The HBA port World Wide Name (WWN) 
[*] The HBA node WWN 
[*] The firmware version 
[*] The fabric name 
[*] The manufacturer of the HBA 
[*] The serial number of the HBA 
[*] The hardware, driver, and read-only memory (ROM) versions 
[*] The product and vendor identification codes 
[*] HBA port statistics - such as frames and words transmitted and  received, synchronization and signal loss counts, and link failures  count 
[*] The zones to which the HBA belongs 
[/LIST]
   
To see the HBA general info, just select the HBA you want to see. To see the details, right-click that HBA and select Properties...

---

