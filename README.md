# Windows Defender Configuration Analysis

In this project I analyze and update a system's Windows Defender antivirus and firewall configurations. I will complete tasks such as updating threat definitions, running antivirus scans, and configuring inbound/outbound network traffic rules so that the system is best protected against known vulnerabilities. 

## Table of Contents

1. [Part 1: Windows Defender Antivirus](#part-1-windows-defender-antivirus)
2. [Part 2: Windows Defender Firewall](#part-2-windows-defender-firewall)
3. [Summary](#summary)

## Part 1: Windows Defender Antivirus

### Identify any current threats 

First I will assess the current state of the system's Windows antivirus and its configurations. 

These settings can be found by navigating through: 
	1. Click the Windows *Start* button 
	2. Select *Settings* 
	3. Scroll down and select *Update & Security*
	4. Select *Virus and threat protection*

![](Images/Pasted%20image%2020230722130926.png)

The virus and threat protection window provides four different features: 
	1. Current threats 
	2. Virus and threat protection settings
	3. Virus and threat protection updates
	4. Ransomware protection

The **Current threats** section shows that the system has not been scanned for a few years and will need a scan as soon as possible. 

### Update threat definitions

Before running any scans, it is important to ensure that the system's **threat definitions** are up to date as these contain threat intelligence and rules on the latest vulnerabilities. Running a scan with outdated threat definitions could result in a threat going undetected. 

In the **Virus & threat protection updates** feature, I run a check for updates to ensure that the system has the latest threat definitions. 

![](Images/Pasted%20image%2020230722132703.png)

### Run antivirus scans

Because of the length of time since the last scan, this system will benefit from a full scan. Windows Security provides tools for quick and custom scans that I will perform before the full scan. 

For this system I will run a: 
	1. Quick scan 
	2. Custom scan for only the downloads folder 
	3. Full scan

Performing a scan will scan files based on the newly updated threat definitions, and after each scan I verify that no threats were found, quarantined, or allowed: 

![](Images/Pasted%20image%2020230722132949.png)

## Part 2: Windows Defender Firewall

### Identify and configure firewall networks 

To view the systems current firewall configurations, I navigate to the **Firewall & network protection**section of **Windows Security**.

While there I verify that each of the firewall network protections are enabled: 
	1. Domain
	2. Private
	3. Public

![](Images/Pasted%20image%2020230722150418.png)

Each one is enabled and currently does not have incoming connections blocked, as expected, and the only active network is a public network: 

![](Images/Pasted%20image%2020230722150526.png)

### Analyze and update firewall rules

Using the **Allow an app through firewall** option in the **Firewall & network protection** settings, I analyze the currently allowed apps that can communicate through the firewall. 

![](Images/Pasted%20image%2020230722150832.png)

In this list I can see that Mozilla Firefox is currently only allowed to communicate on private networks: 

![](Images/Pasted%20image%2020230722150943.png)

I enable this app and allow it to communicate on public networks as well. 

### Configure advanced security firewall rules

Next I will navigate to the advanced security firewall rules where I can allow/deny inbound and outbound traffic. 

![](Images/Pasted%20image%2020230722151808.png)

For this project I want to: 
	- Allow Key Management Service on domain and private networks 
	- Block Key Management Service on public networks
	- Block Windows Remote Management on public networks

Before we enable Key Management Service I want to verify the above rules are in place by navigating to its **Advanced** properties. 

First I will edit the existing Key Management Service **allow** rule to allow only domain and private networks.

![](Images/Pasted%20image%2020230722153113.png)

![](Images/Pasted%20image%2020230722152423.png)

Then I will create a similar **block** rule that will block the public networks. 

![](Images/Pasted%20image%2020230722152856.png)
![](Images/Pasted%20image%2020230722153018.png)

In the main panel I can confirm these were properly created and enabled: 

![](Images/Pasted%20image%2020230722153507.png)

Finally, I edit the existing Windows Remote Management public rule to instead block all communications: 

![](Images/Pasted%20image%2020230722153812.png)

## Summary

In this project I analyzed and configured a system's existing Windows Defender Antivirus and Firewall settings. Based on the existing configurations I completed various tasks such as: 

* Update Windows Defender Antivirus threat definitions
* Run quick, full, and custom antivirus scans
* Review antivirus threat history including quarantined and allowed threats
* Configure allow/block firewall rules using Windows Defender Firewall with and without advanced security

Now that these configurations are up to date, the system is much better protected against the latest known vulnerabilities defined by Microsoft and from unwanted network traffic. 