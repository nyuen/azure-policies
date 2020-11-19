# Prevent Internet egress

This repository highlights multiple options to block internet access when creating a Vnet. In this scenario a central team creates a VNet and lets product team implement their Subnets and NSGs (with network contributor access for subnets).

Preventing egress can be achieved with the following options:

* NSG - adding a deny outbound rule at the subnet level
* UDR - using Route Tables
  * Option 1 - with a centrally managed firewall (recommended)
  * Option 2 - use a route for the Gateway Last Resort 0.0.0.0/0 with a next hop set to None - effectively dropping the traffic

The repository is split in multiple policies:

* append-nsg-no-outbound-internet: adds a default security rule to deny outbound internet
* enforce-rt-vnet; enforce a default UDR if the VNet is not tagged with zone:internet
* deny-nsg-outbound-allow-internet: deny subnets with an allow internet outbound security rule 

