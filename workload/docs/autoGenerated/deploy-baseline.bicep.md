# AVD Accelerator - Baseline Deployment

AVD Accelerator - Deployment Baseline

## Parameters

Parameter name | Required | Description
-------------- | -------- | -----------
deploymentPrefix | No       | The name of the resource group to deploy. (Default: AVD1)
deploymentEnvironment | No       | The name of the resource group to deploy. (Default: Dev)
diskEncryptionKeyExpirationInDays | No       | This value is used to set the expiration date on the disk encryption key. (Default: 60)
avdSessionHostLocation | Yes      | Required. Location where to deploy compute services.
avdManagementPlaneLocation | Yes      | Required. Location where to deploy AVD management plane.
avdWorkloadSubsId | No       | AVD workload subscription ID, multiple subscriptions scenario. (Default: "")
avdServicePrincipalObjectId | No       | Azure Virtual Desktop Enterprise Application object ID (Enterprise app name: Azure Virtual Desktop) . (Default: "")
avdArmServicePrincipalObjectId | No       | Azure Virtual Desktop ARM Enterprise Application Object Id (Enterprise app name: Azure Virtual Desktop ARM Provider). Required for the deployment of App Attach File Share with EntraID identity provider. (Default: "")
avdVmLocalUserName | Yes      | AVD session host local username.
avdVmLocalUserPassword | Yes      | AVD session host local password.
avdIdentityServiceProvider | No       | Required, The service providing domain services for Azure Virtual Desktop. (Default: ADDS)
createIntuneEnrollment | No       | Required, Enroll session hosts on Intune. (Default: false)
avdSecurityGroups | No       | Optional. Identity ID(s) to grant RBAC role to access AVD application group and NTFS permissions. (Default: [])
identityDomainName | No       | FQDN of on-premises AD domain, used for FSLogix storage configuration and NTFS setup. (Default: "none")
identityDomainGuid | No       | GUID of on-premises AD domain, used for FSLogix storage configuration and NTFS setup. (Default: "")
avdDomainJoinUserName | No       | AVD session host domain join user principal name. (Default: "none")
avdDomainJoinUserPassword | No       | AVD session host domain join password. (Default: "none")
avdOuPath      | No       | OU path to join AVd VMs. (Default: "")
avdHostPoolType | No       | AVD host pool type. (Default: Pooled)
hostPoolPreferredAppGroupType | No       | Optional. The type of preferred application group type, default to Desktop Application Group.
hostPoolPublicNetworkAccess | No       | Enables or Disables public network access on the host pool. (Default: Enabled.)
workspacePublicNetworkAccess | No       | Default to Enabled. Enables or Disables public network access on the workspace.
avdPersonalAssignType | No       | AVD host pool type. (Default: Automatic)
avdHostPoolLoadBalancerType | No       | AVD host pool load balacing type. (Default: BreadthFirst)
hostPoolMaxSessions | No       | AVD host pool maximum number of user sessions per session host. (Default: 8)
avdStartVmOnConnect | No       | AVD host pool start VM on Connect. (Default: true)
avdHostPoolRdpProperties | No       | AVD host pool Custom RDP properties. (Default: audiocapturemode:i:1;audiomode:i:0;drivestoredirect:s:;redirectclipboard:i:1;redirectcomports:i:1;redirectprinters:i:1;redirectsmartcards:i:1;screen mode id:i:2)
avdDeployScalingPlan | No       | AVD deploy scaling plan. (Default: true)
createAvdVnet  | No       | Create new virtual network. (Default: true)
existingVnetAvdSubnetResourceId | No       | Existing virtual network subnet for AVD. (Default: "")
existingVnetPrivateEndpointSubnetResourceId | No       | Existing virtual network subnet for private endpoints. (Default: "")
existingHubVnetResourceId | No       | Existing hub virtual network for perring. (Default: "")
avdVnetworkAddressPrefixes | No       | AVD virtual network address prefixes. (Default: 10.10.0.0/16)
vNetworkAvdSubnetAddressPrefix | No       | AVD virtual network subnet address prefix. (Default: 10.10.1.0/24)
vNetworkPrivateEndpointSubnetAddressPrefix | No       | private endpoints virtual network subnet address prefix. (Default: 10.10.2.0/27)
customDnsIps   | No       | custom DNS servers IPs. (Default: "")
deployDDoSNetworkProtection | No       | Deploy DDoS Network Protection for virtual network. (Default: true)
deployPrivateEndpointKeyvaultStorage | No       | Deploy private endpoints for key vault and storage. (Default: true)
deployAvdPrivateLinkService | No       | Deploys the private link for AVD. Requires resource provider registration or re-registration. (Default: false)
createPrivateDnsZones | No       | Create new  Azure private DNS zones for private endpoints. (Default: true)
avdVnetPrivateDnsZoneConnectionResourceId | No       | The ResourceID of the AVD Private DNS Zone for Connection. (privatelink.wvd.azure.com). Only required if createPrivateDNSZones is set to false.
avdVnetPrivateDnsZoneDiscoveryResourceId | No       | The ResourceID of the AVD Private DNS Zone for Discovery. (privatelink-global.wvd.azure.com). Only required if createPrivateDNSZones is set to false.
avdVnetPrivateDnsZoneFilesId | No       | Use existing Azure private DNS zone for Azure files. (Default: "")
avdVnetPrivateDnsZoneKeyvaultId | No       | Use existing Azure private DNS zone for key vault privatelink.vaultcore.azure.net or privatelink.vaultcore.usgovcloudapi.net. (Default: "")
vNetworkGatewayOnHub | No       | Does the hub contains a virtual network gateway. (Default: false)
createAvdFslogixDeployment | No       | Deploy Fslogix setup. (Default: true)
createAppAttachDeployment | No       | Deploy App Attach setup. (Default: false)
fslogixFileShareQuotaSize | No       | Fslogix file share size. (Default: 1)
appAttachFileShareQuotaSize | No       | App Attach file share size. (Default: 1)
avdDeploySessionHosts | No       | Deploy new session hosts. (Default: true)
deployGpuPolicies | No       | Deploy VM GPU extension policies. (Default: false)
avdDeployMonitoring | No       | Deploy AVD monitoring resources and setings. (Default: false)
deployAlaWorkspace | No       | Deploy AVD Azure log analytics workspace. (Default: true)
deployCustomPolicyMonitoring | No       | Create and assign custom Azure Policy for diagnostic settings for the AVD Log Analytics workspace. (Default: false)
avdAlaWorkspaceDataRetention | No       | AVD Azure log analytics workspace data retention. (Default: 90)
alaExistingWorkspaceResourceId | No       | Existing Azure log analytics workspace resource ID to connect to. (Default: "")
avdDeploySessionHostsCount | No       | Quantity of session hosts to deploy. (Default: 1)
avdSessionHostCountIndex | No       | The session host number to begin with for the deployment. This is important when adding virtual machines to ensure the names do not conflict. (Default: 1)
availability   | No       | When true VMs are distributed across availability zones, when set to false, VMs will be deployed at regional level.
availabilityZones | No       | The Availability Zones to use for the session hosts.
zoneRedundantStorage | No       | When true, Zone Redundant Storage (ZRS) is used, when set to false, Locally Redundant Storage (LRS) is used. (Default: false)
fslogixStoragePerformance | No       | Storage account SKU for FSLogix storage. Recommended tier is Premium (Default: Premium)
appAttachStoragePerformance | No       | Storage account SKU for App Attach storage. Recommended tier is Premium. (Default: Premium)
diskZeroTrust  | No       | Enables a zero trust configuration on the session host disks. (Default: false)
avdSessionHostsSize | No       | Session host VM size. (Default: Standard_D4ads_v5)
avdSessionHostDiskType | No       | OS disk type for session host. (Default: Premium_LRS)
customOsDiskSizeGB | No       | Optional. Custom OS Disk Size.
enableAcceleratedNetworking | No       | Enables accelerated Networking on the session hosts. If using a Azure Compute Gallery Image, the Image Definition must have been configured with the \'isAcceleratedNetworkSupported\' property set to \'true\'. 
securityType   | No       | Specifies the securityType of the virtual machine. "ConfidentialVM" and "TrustedLaunch" require a Gen2 Image. (Default: TrustedLaunch)
secureBootEnabled | No       | Specifies whether secure boot should be enabled on the virtual machine. This parameter is part of the UefiSettings. securityType should be set to TrustedLaunch or ConfidentialVM to enable UefiSettings. (Default: true)
vTpmEnabled    | No       | Specifies whether vTPM should be enabled on the virtual machine. This parameter is part of the UefiSettings. securityType should be set to TrustedLaunch or ConfidentialVM to enable UefiSettings. (Default: true)
useSharedImage | No       | Set to deploy image from Azure Compute Gallery. (Default: false)
mpImageOffer   | No       | AVD OS image offer. (Default: Office-365)
mpImageSku     | No       | AVD OS image SKU. (Default: win11-24h2-avd-m365)
avdCustomImageDefinitionId | No       | Source custom image ID. (Default: "")
managementVmOsImage | No       | Management VM image SKU (Default: winServer_2022_Datacenter_smalldisk_g2)
storageOuPath  | No       | OU name for Azure Storage Account. It is recommended to create a new AD Organizational Unit (OU) in AD and disable password expiration policy on computer accounts or service logon accounts accordingly.  (Default: "")
avdUseCustomNaming | No       | AVD resources custom naming. (Default: false)
avdServiceObjectsRgCustomName | No       | AVD service resources resource group custom name. (Default: rg-avd-app1-dev-use2-service-objects)
avdNetworkObjectsRgCustomName | No       | AVD network resources resource group custom name. (Default: rg-avd-app1-dev-use2-network)
avdComputeObjectsRgCustomName | No       | AVD network resources resource group custom name. (Default: rg-avd-app1-dev-use2-pool-compute)
avdStorageObjectsRgCustomName | No       | AVD network resources resource group custom name. (Default: rg-avd-app1-dev-use2-storage)
avdMonitoringRgCustomName | No       | AVD monitoring resource group custom name. (Default: rg-avd-dev-use2-monitoring)
avdVnetworkCustomName | No       | AVD virtual network custom name. (Default: vnet-app1-dev-use2-001)
avdAlaWorkspaceCustomName | No       | AVD Azure log analytics workspace custom name. (Default: log-avd-app1-dev-use2)
avdVnetworkSubnetCustomName | No       | AVD virtual network subnet custom name. (Default: snet-avd-app1-dev-use2-001)
privateEndpointVnetworkSubnetCustomName | No       | private endpoints virtual network subnet custom name. (Default: snet-pe-app1-dev-use2-001)
avdNetworksecurityGroupCustomName | No       | AVD network security group custom name. (Default: nsg-avd-app1-dev-use2-001)
privateEndpointNetworksecurityGroupCustomName | No       | Private endpoint network security group custom name. (Default: nsg-pe-app1-dev-use2-001)
avdRouteTableCustomName | No       | AVD route table custom name. (Default: route-avd-app1-dev-use2-001)
privateEndpointRouteTableCustomName | No       | Private endpoint route table custom name. (Default: route-avd-app1-dev-use2-001)
avdApplicationSecurityGroupCustomName | No       | AVD application security custom name. (Default: asg-app1-dev-use2-001)
avdWorkSpaceCustomName | No       | AVD workspace custom name. (Default: vdws-app1-dev-use2-001)
avdWorkSpaceCustomFriendlyName | No       | AVD workspace custom friendly (Display) name. (Default: App1 - Dev - East US 2 - 001)
avdHostPoolCustomName | No       | AVD host pool custom name. (Default: vdpool-app1-dev-use2-001)
avdHostPoolCustomFriendlyName | No       | AVD host pool custom friendly (Display) name. (Default: App1 - East US - Dev - 001)
avdScalingPlanCustomName | No       | AVD scaling plan custom name. (Default: vdscaling-app1-dev-use2-001)
avdApplicationGroupCustomName | No       | AVD desktop application group custom name. (Default: vdag-desktop-app1-dev-use2-001)
avdApplicationGroupCustomFriendlyName | No       | AVD desktop application group custom friendly (Display) name. (Default: Desktops - App1 - East US - Dev - 001)
avdSessionHostCustomNamePrefix | No       | AVD session host prefix custom name. (Default: vmapp1duse2)
storageAccountPrefixCustomName | No       | AVD FSLogix and App Attach storage account prefix custom name. (Default: st)
fslogixFileShareCustomName | No       | FSLogix file share name. (Default: fslogix-pc-app1-dev-001)
appAttachFileShareCustomName | No       | App Attach file share name. (Default: appa-app1-dev-001)
avdWrklKvPrefixCustomName | No       | AVD keyvault prefix custom name (with Zero Trust to store credentials to domain join and local admin). (Default: kv-sec)
ztDiskEncryptionSetCustomNamePrefix | No       | AVD disk encryption set custom name. (Default: des-zt)
ztKvPrefixCustomName | No       | AVD key vault custom name for zero trust and store store disk encryption key (Default: kv-key)
createResourceTags | No       | Apply tags on resources and resource groups. (Default: false)
workloadNameTag | No       | The name of workload for tagging purposes. (Default: Contoso-Workload)
workloadTypeTag | No       | Reference to the size of the VM for your workloads (Default: Light)
dataClassificationTag | No       | Sensitivity of data hosted (Default: Non-business)
departmentTag  | No       | Department that owns the deployment, (Dafult: Contoso-AVD)
workloadCriticalityTag | No       | Criticality of the workload. (Default: Low)
workloadCriticalityCustomValueTag | No       | Tag value for custom criticality value. (Default: Contoso-Critical)
applicationNameTag | No       | Details about the application.
workloadSlaTag | No       | Service level agreement level of the worload. (Contoso-SLA)
opsTeamTag     | No       | Team accountable for day-to-day operations. (workload-admins@Contoso.com)
ownerTag       | No       | Organizational owner of the AVD deployment. (Default: workload-owner@Contoso.com)
costCenterTag  | No       | Cost center of owner team. (Default: Contoso-CC)
time           | No       | Do not modify, used to set unique value for resource deployment.
enableTelemetry | No       | Enable usage and telemetry feedback to Microsoft.
enableKvPurgeProtection | No       | Enable purge protection for the keyvaults. (Default: true)
deployAntiMalwareExt | No       | Deploys anti malware extension on session hosts. (Default: true)
customStaticRoutes | No       | Additional customer-provided static routes to be added to the route tables.
deployDefender | No       | Enable Microsoft Defender on the subscription. (Default: false)
enableDefForServers | No       | Enable Microsoft Defender for servers. (Default: true)
enableDefForStorage | No       | Enable Microsoft Defender for storage. (Default: true)
enableDefForKeyVault | No       | Enable Microsoft Defender for Key Vault. (Default: true)
enableDefForArm | No       | Enable Microsoft Defender for Azure Resource Manager. (Default: true)

### deploymentPrefix

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The name of the resource group to deploy. (Default: AVD1)

- Default value: `AVD1`

### deploymentEnvironment

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The name of the resource group to deploy. (Default: Dev)

- Default value: `Dev`

- Allowed values: `Dev`, `Test`, `Prod`

### diskEncryptionKeyExpirationInDays

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

This value is used to set the expiration date on the disk encryption key. (Default: 60)

- Default value: `60`

### avdSessionHostLocation

![Parameter Setting](https://img.shields.io/badge/parameter-required-orange?style=flat-square)

Required. Location where to deploy compute services.

### avdManagementPlaneLocation

![Parameter Setting](https://img.shields.io/badge/parameter-required-orange?style=flat-square)

Required. Location where to deploy AVD management plane.

### avdWorkloadSubsId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD workload subscription ID, multiple subscriptions scenario. (Default: "")

### avdServicePrincipalObjectId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Azure Virtual Desktop Enterprise Application object ID (Enterprise app name: Azure Virtual Desktop) . (Default: "")

### avdArmServicePrincipalObjectId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Azure Virtual Desktop ARM Enterprise Application Object Id (Enterprise app name: Azure Virtual Desktop ARM Provider). Required for the deployment of App Attach File Share with EntraID identity provider. (Default: "")

### avdVmLocalUserName

![Parameter Setting](https://img.shields.io/badge/parameter-required-orange?style=flat-square)

AVD session host local username.

### avdVmLocalUserPassword

![Parameter Setting](https://img.shields.io/badge/parameter-required-orange?style=flat-square)

AVD session host local password.

### avdIdentityServiceProvider

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Required, The service providing domain services for Azure Virtual Desktop. (Default: ADDS)

- Default value: `ADDS`

- Allowed values: `ADDS`, `EntraDS`, `EntraID`, `EntraIDKerberos`

### createIntuneEnrollment

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Required, Enroll session hosts on Intune. (Default: false)

- Default value: `False`

### avdSecurityGroups

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Optional. Identity ID(s) to grant RBAC role to access AVD application group and NTFS permissions. (Default: [])

### identityDomainName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

FQDN of on-premises AD domain, used for FSLogix storage configuration and NTFS setup. (Default: "none")

- Default value: `none`

### identityDomainGuid

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

GUID of on-premises AD domain, used for FSLogix storage configuration and NTFS setup. (Default: "")

### avdDomainJoinUserName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD session host domain join user principal name. (Default: "none")

- Default value: `none`

### avdDomainJoinUserPassword

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD session host domain join password. (Default: "none")

- Default value: `none`

### avdOuPath

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

OU path to join AVd VMs. (Default: "")

### avdHostPoolType

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD host pool type. (Default: Pooled)

- Default value: `Pooled`

- Allowed values: `Personal`, `Pooled`

### hostPoolPreferredAppGroupType

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Optional. The type of preferred application group type, default to Desktop Application Group.

- Default value: `Desktop`

- Allowed values: `Desktop`, `RemoteApp`

### hostPoolPublicNetworkAccess

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enables or Disables public network access on the host pool. (Default: Enabled.)

- Default value: `Enabled`

- Allowed values: `Disabled`, `Enabled`, `EnabledForClientsOnly`, `EnabledForSessionHostsOnly`

### workspacePublicNetworkAccess

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Default to Enabled. Enables or Disables public network access on the workspace.

- Default value: `Enabled`

- Allowed values: `Disabled`, `Enabled`

### avdPersonalAssignType

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD host pool type. (Default: Automatic)

- Default value: `Automatic`

- Allowed values: `Automatic`, `Direct`

### avdHostPoolLoadBalancerType

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD host pool load balacing type. (Default: BreadthFirst)

- Default value: `BreadthFirst`

- Allowed values: `BreadthFirst`, `DepthFirst`

### hostPoolMaxSessions

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD host pool maximum number of user sessions per session host. (Default: 8)

- Default value: `8`

### avdStartVmOnConnect

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD host pool start VM on Connect. (Default: true)

- Default value: `True`

### avdHostPoolRdpProperties

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD host pool Custom RDP properties. (Default: audiocapturemode:i:1;audiomode:i:0;drivestoredirect:s:;redirectclipboard:i:1;redirectcomports:i:1;redirectprinters:i:1;redirectsmartcards:i:1;screen mode id:i:2)

- Default value: `audiocapturemode:i:1;audiomode:i:0;drivestoredirect:s:;redirectclipboard:i:1;redirectcomports:i:1;redirectprinters:i:1;redirectsmartcards:i:1;screen mode id:i:2`

### avdDeployScalingPlan

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD deploy scaling plan. (Default: true)

- Default value: `True`

### createAvdVnet

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Create new virtual network. (Default: true)

- Default value: `True`

### existingVnetAvdSubnetResourceId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Existing virtual network subnet for AVD. (Default: "")

### existingVnetPrivateEndpointSubnetResourceId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Existing virtual network subnet for private endpoints. (Default: "")

### existingHubVnetResourceId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Existing hub virtual network for perring. (Default: "")

### avdVnetworkAddressPrefixes

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD virtual network address prefixes. (Default: 10.10.0.0/16)

- Default value: `10.10.0.0/16`

### vNetworkAvdSubnetAddressPrefix

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD virtual network subnet address prefix. (Default: 10.10.1.0/24)

- Default value: `10.10.1.0/24`

### vNetworkPrivateEndpointSubnetAddressPrefix

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

private endpoints virtual network subnet address prefix. (Default: 10.10.2.0/27)

- Default value: `10.10.2.0/27`

### customDnsIps

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

custom DNS servers IPs. (Default: "")

### deployDDoSNetworkProtection

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploy DDoS Network Protection for virtual network. (Default: true)

- Default value: `False`

### deployPrivateEndpointKeyvaultStorage

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploy private endpoints for key vault and storage. (Default: true)

- Default value: `True`

### deployAvdPrivateLinkService

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploys the private link for AVD. Requires resource provider registration or re-registration. (Default: false)

- Default value: `False`

### createPrivateDnsZones

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Create new  Azure private DNS zones for private endpoints. (Default: true)

- Default value: `True`

### avdVnetPrivateDnsZoneConnectionResourceId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The ResourceID of the AVD Private DNS Zone for Connection. (privatelink.wvd.azure.com). Only required if createPrivateDNSZones is set to false.

### avdVnetPrivateDnsZoneDiscoveryResourceId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The ResourceID of the AVD Private DNS Zone for Discovery. (privatelink-global.wvd.azure.com). Only required if createPrivateDNSZones is set to false.

### avdVnetPrivateDnsZoneFilesId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Use existing Azure private DNS zone for Azure files. (Default: "")

### avdVnetPrivateDnsZoneKeyvaultId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Use existing Azure private DNS zone for key vault privatelink.vaultcore.azure.net or privatelink.vaultcore.usgovcloudapi.net. (Default: "")

### vNetworkGatewayOnHub

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Does the hub contains a virtual network gateway. (Default: false)

- Default value: `False`

### createAvdFslogixDeployment

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploy Fslogix setup. (Default: true)

- Default value: `True`

### createAppAttachDeployment

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploy App Attach setup. (Default: false)

- Default value: `False`

### fslogixFileShareQuotaSize

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Fslogix file share size. (Default: 1)

- Default value: `1`

### appAttachFileShareQuotaSize

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

App Attach file share size. (Default: 1)

- Default value: `1`

### avdDeploySessionHosts

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploy new session hosts. (Default: true)

- Default value: `True`

### deployGpuPolicies

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploy VM GPU extension policies. (Default: false)

- Default value: `False`

### avdDeployMonitoring

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploy AVD monitoring resources and setings. (Default: false)

- Default value: `False`

### deployAlaWorkspace

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploy AVD Azure log analytics workspace. (Default: true)

- Default value: `True`

### deployCustomPolicyMonitoring

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Create and assign custom Azure Policy for diagnostic settings for the AVD Log Analytics workspace. (Default: false)

- Default value: `False`

### avdAlaWorkspaceDataRetention

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD Azure log analytics workspace data retention. (Default: 90)

- Default value: `90`

### alaExistingWorkspaceResourceId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Existing Azure log analytics workspace resource ID to connect to. (Default: "")

### avdDeploySessionHostsCount

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Quantity of session hosts to deploy. (Default: 1)

- Default value: `1`

### avdSessionHostCountIndex

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The session host number to begin with for the deployment. This is important when adding virtual machines to ensure the names do not conflict. (Default: 1)

- Default value: `1`

### availability

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

When true VMs are distributed across availability zones, when set to false, VMs will be deployed at regional level.

- Default value: `None`

- Allowed values: `None`, `AvailabilityZones`

### availabilityZones

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The Availability Zones to use for the session hosts.

- Default value: `1 2 3`

- Allowed values: `1`, `2`, `3`

### zoneRedundantStorage

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

When true, Zone Redundant Storage (ZRS) is used, when set to false, Locally Redundant Storage (LRS) is used. (Default: false)

- Default value: `False`

### fslogixStoragePerformance

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Storage account SKU for FSLogix storage. Recommended tier is Premium (Default: Premium)

- Default value: `Premium`

- Allowed values: `Standard`, `Premium`

### appAttachStoragePerformance

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Storage account SKU for App Attach storage. Recommended tier is Premium. (Default: Premium)

- Default value: `Premium`

- Allowed values: `Standard`, `Premium`

### diskZeroTrust

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enables a zero trust configuration on the session host disks. (Default: false)

- Default value: `False`

### avdSessionHostsSize

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Session host VM size. (Default: Standard_D4ads_v5)

- Default value: `Standard_D4ads_v5`

### avdSessionHostDiskType

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

OS disk type for session host. (Default: Premium_LRS)

- Default value: `Premium_LRS`

### customOsDiskSizeGB

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Optional. Custom OS Disk Size.

- Default value: `0`

### enableAcceleratedNetworking

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enables accelerated Networking on the session hosts.
If using a Azure Compute Gallery Image, the Image Definition must have been configured with
the \'isAcceleratedNetworkSupported\' property set to \'true\'.


- Default value: `True`

### securityType

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Specifies the securityType of the virtual machine. "ConfidentialVM" and "TrustedLaunch" require a Gen2 Image. (Default: TrustedLaunch)

- Default value: `TrustedLaunch`

- Allowed values: `Standard`, `TrustedLaunch`

### secureBootEnabled

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Specifies whether secure boot should be enabled on the virtual machine. This parameter is part of the UefiSettings. securityType should be set to TrustedLaunch or ConfidentialVM to enable UefiSettings. (Default: true)

- Default value: `True`

### vTpmEnabled

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Specifies whether vTPM should be enabled on the virtual machine. This parameter is part of the UefiSettings. securityType should be set to TrustedLaunch or ConfidentialVM to enable UefiSettings. (Default: true)

- Default value: `True`

### useSharedImage

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Set to deploy image from Azure Compute Gallery. (Default: false)

- Default value: `False`

### mpImageOffer

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD OS image offer. (Default: Office-365)

- Default value: `Office-365`

### mpImageSku

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD OS image SKU. (Default: win11-24h2-avd-m365)

- Default value: `win11-24h2-avd-m365`

### avdCustomImageDefinitionId

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Source custom image ID. (Default: "")

### managementVmOsImage

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Management VM image SKU (Default: winServer_2022_Datacenter_smalldisk_g2)

- Default value: `winServer_2022_Datacenter_smalldisk_g2`

### storageOuPath

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

OU name for Azure Storage Account. It is recommended to create a new AD Organizational Unit (OU) in AD and disable password expiration policy on computer accounts or service logon accounts accordingly.  (Default: "")

### avdUseCustomNaming

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD resources custom naming. (Default: false)

- Default value: `False`

### avdServiceObjectsRgCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD service resources resource group custom name. (Default: rg-avd-app1-dev-use2-service-objects)

- Default value: `rg-avd-app1-dev-use2-service-objects`

### avdNetworkObjectsRgCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD network resources resource group custom name. (Default: rg-avd-app1-dev-use2-network)

- Default value: `rg-avd-app1-dev-use2-network`

### avdComputeObjectsRgCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD network resources resource group custom name. (Default: rg-avd-app1-dev-use2-pool-compute)

- Default value: `rg-avd-app1-dev-use2-pool-compute`

### avdStorageObjectsRgCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD network resources resource group custom name. (Default: rg-avd-app1-dev-use2-storage)

- Default value: `rg-avd-app1-dev-use2-storage`

### avdMonitoringRgCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD monitoring resource group custom name. (Default: rg-avd-dev-use2-monitoring)

- Default value: `rg-avd-dev-use2-monitoring`

### avdVnetworkCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD virtual network custom name. (Default: vnet-app1-dev-use2-001)

- Default value: `vnet-app1-dev-use2-001`

### avdAlaWorkspaceCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD Azure log analytics workspace custom name. (Default: log-avd-app1-dev-use2)

- Default value: `log-avd-app1-dev-use2`

### avdVnetworkSubnetCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD virtual network subnet custom name. (Default: snet-avd-app1-dev-use2-001)

- Default value: `snet-avd-app1-dev-use2-001`

### privateEndpointVnetworkSubnetCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

private endpoints virtual network subnet custom name. (Default: snet-pe-app1-dev-use2-001)

- Default value: `snet-pe-app1-dev-use2-001`

### avdNetworksecurityGroupCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD network security group custom name. (Default: nsg-avd-app1-dev-use2-001)

- Default value: `nsg-avd-app1-dev-use2-001`

### privateEndpointNetworksecurityGroupCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Private endpoint network security group custom name. (Default: nsg-pe-app1-dev-use2-001)

- Default value: `nsg-pe-app1-dev-use2-001`

### avdRouteTableCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD route table custom name. (Default: route-avd-app1-dev-use2-001)

- Default value: `route-avd-app1-dev-use2-001`

### privateEndpointRouteTableCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Private endpoint route table custom name. (Default: route-avd-app1-dev-use2-001)

- Default value: `route-pe-app1-dev-use2-001`

### avdApplicationSecurityGroupCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD application security custom name. (Default: asg-app1-dev-use2-001)

- Default value: `asg-app1-dev-use2-001`

### avdWorkSpaceCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD workspace custom name. (Default: vdws-app1-dev-use2-001)

- Default value: `vdws-app1-dev-use2-001`

### avdWorkSpaceCustomFriendlyName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD workspace custom friendly (Display) name. (Default: App1 - Dev - East US 2 - 001)

- Default value: `App1 - Dev - East US 2 - 001`

### avdHostPoolCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD host pool custom name. (Default: vdpool-app1-dev-use2-001)

- Default value: `vdpool-app1-dev-use2-001`

### avdHostPoolCustomFriendlyName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD host pool custom friendly (Display) name. (Default: App1 - East US - Dev - 001)

- Default value: `App1 - Dev - East US 2 - 001`

### avdScalingPlanCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD scaling plan custom name. (Default: vdscaling-app1-dev-use2-001)

- Default value: `vdscaling-app1-dev-use2-001`

### avdApplicationGroupCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD desktop application group custom name. (Default: vdag-desktop-app1-dev-use2-001)

- Default value: `vdag-desktop-app1-dev-use2-001`

### avdApplicationGroupCustomFriendlyName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD desktop application group custom friendly (Display) name. (Default: Desktops - App1 - East US - Dev - 001)

- Default value: `Desktops - App1 - Dev - East US 2 - 001`

### avdSessionHostCustomNamePrefix

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD session host prefix custom name. (Default: vmapp1duse2)

- Default value: `vmapp1duse2`

### storageAccountPrefixCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD FSLogix and App Attach storage account prefix custom name. (Default: st)

- Default value: `st`

### fslogixFileShareCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

FSLogix file share name. (Default: fslogix-pc-app1-dev-001)

- Default value: `fslogix-pc-app1-dev-use2-001`

### appAttachFileShareCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

App Attach file share name. (Default: appa-app1-dev-001)

- Default value: `appa-app1-dev-use2-001`

### avdWrklKvPrefixCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD keyvault prefix custom name (with Zero Trust to store credentials to domain join and local admin). (Default: kv-sec)

- Default value: `kv-sec`

### ztDiskEncryptionSetCustomNamePrefix

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD disk encryption set custom name. (Default: des-zt)

- Default value: `des-zt`

### ztKvPrefixCustomName

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

AVD key vault custom name for zero trust and store store disk encryption key (Default: kv-key)

- Default value: `kv-key`

### createResourceTags

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Apply tags on resources and resource groups. (Default: false)

- Default value: `False`

### workloadNameTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

The name of workload for tagging purposes. (Default: Contoso-Workload)

- Default value: `Contoso-Workload`

### workloadTypeTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Reference to the size of the VM for your workloads (Default: Light)

- Default value: `Light`

- Allowed values: ``, `Light`, `Medium`, `High`, `Power`

### dataClassificationTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Sensitivity of data hosted (Default: Non-business)

- Default value: `Non-business`

- Allowed values: ``, `Non-business`, `Public`, `General`, `Confidential`, `Highly-confidential`

### departmentTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Department that owns the deployment, (Dafult: Contoso-AVD)

- Default value: `Contoso-AVD`

### workloadCriticalityTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Criticality of the workload. (Default: Low)

- Default value: `Low`

- Allowed values: ``, `Low`, `Medium`, `High`, `Mission-critical`, `Custom`

### workloadCriticalityCustomValueTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Tag value for custom criticality value. (Default: Contoso-Critical)

- Default value: `Contoso-Critical`

### applicationNameTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Details about the application.

- Default value: `Contoso-App`

### workloadSlaTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Service level agreement level of the worload. (Contoso-SLA)

- Default value: `Contoso-SLA`

### opsTeamTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Team accountable for day-to-day operations. (workload-admins@Contoso.com)

- Default value: `workload-admins@Contoso.com`

### ownerTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Organizational owner of the AVD deployment. (Default: workload-owner@Contoso.com)

- Default value: `workload-owner@Contoso.com`

### costCenterTag

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Cost center of owner team. (Default: Contoso-CC)

- Default value: `Contoso-CC`

### time

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Do not modify, used to set unique value for resource deployment.

- Default value: `[utcNow()]`

### enableTelemetry

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enable usage and telemetry feedback to Microsoft.

- Default value: `True`

### enableKvPurgeProtection

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enable purge protection for the keyvaults. (Default: true)

- Default value: `True`

### deployAntiMalwareExt

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Deploys anti malware extension on session hosts. (Default: true)

- Default value: `True`

### customStaticRoutes

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Additional customer-provided static routes to be added to the route tables.

### deployDefender

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enable Microsoft Defender on the subscription. (Default: false)

- Default value: `False`

### enableDefForServers

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enable Microsoft Defender for servers. (Default: true)

- Default value: `True`

### enableDefForStorage

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enable Microsoft Defender for storage. (Default: true)

- Default value: `True`

### enableDefForKeyVault

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enable Microsoft Defender for Key Vault. (Default: true)

- Default value: `True`

### enableDefForArm

![Parameter Setting](https://img.shields.io/badge/parameter-optional-green?style=flat-square)

Enable Microsoft Defender for Azure Resource Manager. (Default: true)

- Default value: `True`

## Snippets

### Parameter file

```json
{
    "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentParameters.json#",
    "contentVersion": "1.0.0.0",
    "metadata": {
        "template": "workload/bicep/deploy-baseline.json"
    },
    "parameters": {
        "deploymentPrefix": {
            "value": "AVD1"
        },
        "deploymentEnvironment": {
            "value": "Dev"
        },
        "diskEncryptionKeyExpirationInDays": {
            "value": 60
        },
        "avdSessionHostLocation": {
            "value": ""
        },
        "avdManagementPlaneLocation": {
            "value": ""
        },
        "avdWorkloadSubsId": {
            "value": ""
        },
        "avdServicePrincipalObjectId": {
            "value": ""
        },
        "avdArmServicePrincipalObjectId": {
            "value": ""
        },
        "avdVmLocalUserName": {
            "value": ""
        },
        "avdVmLocalUserPassword": {
            "reference": {
                "keyVault": {
                    "id": ""
                },
                "secretName": ""
            }
        },
        "avdIdentityServiceProvider": {
            "value": "ADDS"
        },
        "createIntuneEnrollment": {
            "value": false
        },
        "avdSecurityGroups": {
            "value": []
        },
        "identityDomainName": {
            "value": "none"
        },
        "identityDomainGuid": {
            "value": ""
        },
        "avdDomainJoinUserName": {
            "value": "none"
        },
        "avdDomainJoinUserPassword": {
            "reference": {
                "keyVault": {
                    "id": ""
                },
                "secretName": ""
            }
        },
        "avdOuPath": {
            "value": ""
        },
        "avdHostPoolType": {
            "value": "Pooled"
        },
        "hostPoolPreferredAppGroupType": {
            "value": "Desktop"
        },
        "hostPoolPublicNetworkAccess": {
            "value": "Enabled"
        },
        "workspacePublicNetworkAccess": {
            "value": "Enabled"
        },
        "avdPersonalAssignType": {
            "value": "Automatic"
        },
        "avdHostPoolLoadBalancerType": {
            "value": "BreadthFirst"
        },
        "hostPoolMaxSessions": {
            "value": 8
        },
        "avdStartVmOnConnect": {
            "value": true
        },
        "avdHostPoolRdpProperties": {
            "value": "audiocapturemode:i:1;audiomode:i:0;drivestoredirect:s:;redirectclipboard:i:1;redirectcomports:i:1;redirectprinters:i:1;redirectsmartcards:i:1;screen mode id:i:2"
        },
        "avdDeployScalingPlan": {
            "value": true
        },
        "createAvdVnet": {
            "value": true
        },
        "existingVnetAvdSubnetResourceId": {
            "value": ""
        },
        "existingVnetPrivateEndpointSubnetResourceId": {
            "value": ""
        },
        "existingHubVnetResourceId": {
            "value": ""
        },
        "avdVnetworkAddressPrefixes": {
            "value": "10.10.0.0/16"
        },
        "vNetworkAvdSubnetAddressPrefix": {
            "value": "10.10.1.0/24"
        },
        "vNetworkPrivateEndpointSubnetAddressPrefix": {
            "value": "10.10.2.0/27"
        },
        "customDnsIps": {
            "value": ""
        },
        "deployDDoSNetworkProtection": {
            "value": false
        },
        "deployPrivateEndpointKeyvaultStorage": {
            "value": true
        },
        "deployAvdPrivateLinkService": {
            "value": false
        },
        "createPrivateDnsZones": {
            "value": true
        },
        "avdVnetPrivateDnsZoneConnectionResourceId": {
            "value": ""
        },
        "avdVnetPrivateDnsZoneDiscoveryResourceId": {
            "value": ""
        },
        "avdVnetPrivateDnsZoneFilesId": {
            "value": ""
        },
        "avdVnetPrivateDnsZoneKeyvaultId": {
            "value": ""
        },
        "vNetworkGatewayOnHub": {
            "value": false
        },
        "createAvdFslogixDeployment": {
            "value": true
        },
        "createAppAttachDeployment": {
            "value": false
        },
        "fslogixFileShareQuotaSize": {
            "value": 1
        },
        "appAttachFileShareQuotaSize": {
            "value": 1
        },
        "avdDeploySessionHosts": {
            "value": true
        },
        "deployGpuPolicies": {
            "value": false
        },
        "avdDeployMonitoring": {
            "value": false
        },
        "deployAlaWorkspace": {
            "value": true
        },
        "deployCustomPolicyMonitoring": {
            "value": false
        },
        "avdAlaWorkspaceDataRetention": {
            "value": 90
        },
        "alaExistingWorkspaceResourceId": {
            "value": ""
        },
        "avdDeploySessionHostsCount": {
            "value": 1
        },
        "avdSessionHostCountIndex": {
            "value": 1
        },
        "availability": {
            "value": "None"
        },
        "availabilityZones": {
            "value": [
                "1",
                "2",
                "3"
            ]
        },
        "zoneRedundantStorage": {
            "value": false
        },
        "fslogixStoragePerformance": {
            "value": "Premium"
        },
        "appAttachStoragePerformance": {
            "value": "Premium"
        },
        "diskZeroTrust": {
            "value": false
        },
        "avdSessionHostsSize": {
            "value": "Standard_D4ads_v5"
        },
        "avdSessionHostDiskType": {
            "value": "Premium_LRS"
        },
        "customOsDiskSizeGB": {
            "value": 0
        },
        "enableAcceleratedNetworking": {
            "value": true
        },
        "securityType": {
            "value": "TrustedLaunch"
        },
        "secureBootEnabled": {
            "value": true
        },
        "vTpmEnabled": {
            "value": true
        },
        "useSharedImage": {
            "value": false
        },
        "mpImageOffer": {
            "value": "Office-365"
        },
        "mpImageSku": {
            "value": "win11-24h2-avd-m365"
        },
        "avdCustomImageDefinitionId": {
            "value": ""
        },
        "managementVmOsImage": {
            "value": "winServer_2022_Datacenter_smalldisk_g2"
        },
        "storageOuPath": {
            "value": ""
        },
        "avdUseCustomNaming": {
            "value": false
        },
        "avdServiceObjectsRgCustomName": {
            "value": "rg-avd-app1-dev-use2-service-objects"
        },
        "avdNetworkObjectsRgCustomName": {
            "value": "rg-avd-app1-dev-use2-network"
        },
        "avdComputeObjectsRgCustomName": {
            "value": "rg-avd-app1-dev-use2-pool-compute"
        },
        "avdStorageObjectsRgCustomName": {
            "value": "rg-avd-app1-dev-use2-storage"
        },
        "avdMonitoringRgCustomName": {
            "value": "rg-avd-dev-use2-monitoring"
        },
        "avdVnetworkCustomName": {
            "value": "vnet-app1-dev-use2-001"
        },
        "avdAlaWorkspaceCustomName": {
            "value": "log-avd-app1-dev-use2"
        },
        "avdVnetworkSubnetCustomName": {
            "value": "snet-avd-app1-dev-use2-001"
        },
        "privateEndpointVnetworkSubnetCustomName": {
            "value": "snet-pe-app1-dev-use2-001"
        },
        "avdNetworksecurityGroupCustomName": {
            "value": "nsg-avd-app1-dev-use2-001"
        },
        "privateEndpointNetworksecurityGroupCustomName": {
            "value": "nsg-pe-app1-dev-use2-001"
        },
        "avdRouteTableCustomName": {
            "value": "route-avd-app1-dev-use2-001"
        },
        "privateEndpointRouteTableCustomName": {
            "value": "route-pe-app1-dev-use2-001"
        },
        "avdApplicationSecurityGroupCustomName": {
            "value": "asg-app1-dev-use2-001"
        },
        "avdWorkSpaceCustomName": {
            "value": "vdws-app1-dev-use2-001"
        },
        "avdWorkSpaceCustomFriendlyName": {
            "value": "App1 - Dev - East US 2 - 001"
        },
        "avdHostPoolCustomName": {
            "value": "vdpool-app1-dev-use2-001"
        },
        "avdHostPoolCustomFriendlyName": {
            "value": "App1 - Dev - East US 2 - 001"
        },
        "avdScalingPlanCustomName": {
            "value": "vdscaling-app1-dev-use2-001"
        },
        "avdApplicationGroupCustomName": {
            "value": "vdag-desktop-app1-dev-use2-001"
        },
        "avdApplicationGroupCustomFriendlyName": {
            "value": "Desktops - App1 - Dev - East US 2 - 001"
        },
        "avdSessionHostCustomNamePrefix": {
            "value": "vmapp1duse2"
        },
        "storageAccountPrefixCustomName": {
            "value": "st"
        },
        "fslogixFileShareCustomName": {
            "value": "fslogix-pc-app1-dev-use2-001"
        },
        "appAttachFileShareCustomName": {
            "value": "appa-app1-dev-use2-001"
        },
        "avdWrklKvPrefixCustomName": {
            "value": "kv-sec"
        },
        "ztDiskEncryptionSetCustomNamePrefix": {
            "value": "des-zt"
        },
        "ztKvPrefixCustomName": {
            "value": "kv-key"
        },
        "createResourceTags": {
            "value": false
        },
        "workloadNameTag": {
            "value": "Contoso-Workload"
        },
        "workloadTypeTag": {
            "value": "Light"
        },
        "dataClassificationTag": {
            "value": "Non-business"
        },
        "departmentTag": {
            "value": "Contoso-AVD"
        },
        "workloadCriticalityTag": {
            "value": "Low"
        },
        "workloadCriticalityCustomValueTag": {
            "value": "Contoso-Critical"
        },
        "applicationNameTag": {
            "value": "Contoso-App"
        },
        "workloadSlaTag": {
            "value": "Contoso-SLA"
        },
        "opsTeamTag": {
            "value": "workload-admins@Contoso.com"
        },
        "ownerTag": {
            "value": "workload-owner@Contoso.com"
        },
        "costCenterTag": {
            "value": "Contoso-CC"
        },
        "time": {
            "value": "[utcNow()]"
        },
        "enableTelemetry": {
            "value": true
        },
        "enableKvPurgeProtection": {
            "value": true
        },
        "deployAntiMalwareExt": {
            "value": true
        },
        "customStaticRoutes": {
            "value": []
        },
        "deployDefender": {
            "value": false
        },
        "enableDefForServers": {
            "value": true
        },
        "enableDefForStorage": {
            "value": true
        },
        "enableDefForKeyVault": {
            "value": true
        },
        "enableDefForArm": {
            "value": true
        }
    }
}
```
