# ProportionalPayoutStrategy

*allo-team*

> Proportional Payout Strategy

This strategy allows the allocator to allocate votes to recipients



## Methods

### NATIVE

```solidity
function NATIVE() external view returns (address)
```

Address of the native token




#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | address | undefined |

### allocate

```solidity
function allocate(bytes _data, address _sender) external payable
```



*Only called via Allo.sol by users to allocate to a recipient      this will update some data in this contract to store votes, etc Requirements: This will be determined by the strategy*

#### Parameters

| Name | Type | Description |
|---|---|---|
| _data | bytes | undefined |
| _sender | address | undefined |

### allocationEndTime

```solidity
function allocationEndTime() external view returns (uint256)
```






#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined |

### allocationStartTime

```solidity
function allocationStartTime() external view returns (uint256)
```






#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined |

### distribute

```solidity
function distribute(address[] _recipientIds, bytes _data, address _sender) external nonpayable
```



*This will distribute tokens to recipients NOTE: Most strategies will track a TOTAL amount per recipient, and a PAID amount, and pay the difference.       This contract will need to track the amount paid already, so that it doesn&#39;t double pay Requirements: This will be determined by the strategy*

#### Parameters

| Name | Type | Description |
|---|---|---|
| _recipientIds | address[] | undefined |
| _data | bytes | undefined |
| _sender | address | undefined |

### getAllo

```solidity
function getAllo() external view returns (contract IAllo)
```

================================ =========== Views ============== ================================




#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | contract IAllo | undefined |

### getPayouts

```solidity
function getPayouts(address[] _recipientIds, bytes[] _data) external view returns (struct IStrategy.PayoutSummary[])
```





#### Parameters

| Name | Type | Description |
|---|---|---|
| _recipientIds | address[] | undefined |
| _data | bytes[] | undefined |

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | IStrategy.PayoutSummary[] | Input the values you would send to distribute(), get the amounts each recipient in the array would receive |

### getPoolAmount

```solidity
function getPoolAmount() external view returns (uint256)
```



*returns the amount of tokens in the pool*


#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined |

### getPoolId

```solidity
function getPoolId() external view returns (uint256)
```



*Getter for the &#39;poolId&#39; for this strategy*


#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined |

### getRecipient

```solidity
function getRecipient(address _recipientId) external view returns (struct ProportionalPayoutStrategy.Recipient)
```

Get the recipient



#### Parameters

| Name | Type | Description |
|---|---|---|
| _recipientId | address | Id of the recipient |

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | ProportionalPayoutStrategy.Recipient | undefined |

### getRecipientStatus

```solidity
function getRecipientStatus(address _recipientId) external view returns (enum IStrategy.RecipientStatus)
```



*Returns the status of a recipient probably tracked in a mapping, but will depend on the implementation      for example, the OpenSelfRegistration only maps users to bool, and then assumes Accepted for those      since there is no need for Pending or Rejected*

#### Parameters

| Name | Type | Description |
|---|---|---|
| _recipientId | address | undefined |

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | enum IStrategy.RecipientStatus | undefined |

### getStrategyId

```solidity
function getStrategyId() external view returns (bytes32)
```



*Getter for the &#39;id&#39; of the strategy*


#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | bytes32 | undefined |

### hasAllocated

```solidity
function hasAllocated(uint256) external view returns (bool)
```

nftId =&gt; has allocated



#### Parameters

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined |

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | bool | undefined |

### increasePoolAmount

```solidity
function increasePoolAmount(uint256 _amount) external nonpayable
```

incrases the poolAmount which is set on invoking Allo.fundPool



#### Parameters

| Name | Type | Description |
|---|---|---|
| _amount | uint256 | undefined |

### initialize

```solidity
function initialize(uint256 _poolId, bytes _data) external nonpayable
```

=============================== ========= Initialize ========== ===============================



#### Parameters

| Name | Type | Description |
|---|---|---|
| _poolId | uint256 | undefined |
| _data | bytes | undefined |

### isPoolActive

```solidity
function isPoolActive() external view returns (bool)
```



*whether pool is active*


#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | bool | undefined |

### isValidAllocator

```solidity
function isValidAllocator(address _allocator) external view returns (bool)
```



*Returns whether a allocator is valid or not, will usually be true for all      and will depend on the strategy implementation*

#### Parameters

| Name | Type | Description |
|---|---|---|
| _allocator | address | undefined |

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | bool | undefined |

### maxRecipientsAllowed

```solidity
function maxRecipientsAllowed() external view returns (uint256)
```






#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined |

### nft

```solidity
function nft() external view returns (contract ERC721)
```






#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | contract ERC721 | undefined |

### paidOut

```solidity
function paidOut(address) external view returns (bool)
```

recipientId =&gt; paid out



#### Parameters

| Name | Type | Description |
|---|---|---|
| _0 | address | undefined |

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | bool | undefined |

### recipients

```solidity
function recipients(address) external view returns (address recipientAddress, struct Metadata metadata, enum IStrategy.RecipientStatus recipientStatus, uint256 totalVotesReceived)
```

recipientId =&gt; Recipient



#### Parameters

| Name | Type | Description |
|---|---|---|
| _0 | address | undefined |

#### Returns

| Name | Type | Description |
|---|---|---|
| recipientAddress | address | undefined |
| metadata | Metadata | undefined |
| recipientStatus | enum IStrategy.RecipientStatus | undefined |
| totalVotesReceived | uint256 | undefined |

### recipientsCounter

```solidity
function recipientsCounter() external view returns (uint256)
```






#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined |

### registerRecipient

```solidity
function registerRecipient(bytes _data, address _sender) external payable returns (address)
```



*This is called via Allo.sol to register recipients      it can change their status all the way to Accepted, or to Pending if there are more steps      if there are more steps, additional functions should be added to allow the owner to check      this could also check attestations directly and then Accept Requirements: This will be determined by the strategy*

#### Parameters

| Name | Type | Description |
|---|---|---|
| _data | bytes | undefined |
| _sender | address | undefined |

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | address | undefined |

### setAllocationTime

```solidity
function setAllocationTime(uint256 _allocationStartTime, uint256 _allocationEndTime) external nonpayable
```

Set the allocation start and end timestamps



#### Parameters

| Name | Type | Description |
|---|---|---|
| _allocationStartTime | uint256 | The allocation start timestamp |
| _allocationEndTime | uint256 | The allocation end timestamp |

### totalAllocations

```solidity
function totalAllocations() external view returns (uint256)
```






#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined |



## Events

### Allocated

```solidity
event Allocated(address indexed recipientId, uint256 amount, address token, address sender)
```

Event emitted when a recipient is allocated to



#### Parameters

| Name | Type | Description |
|---|---|---|
| recipientId `indexed` | address | undefined |
| amount  | uint256 | undefined |
| token  | address | undefined |
| sender  | address | undefined |

### AllocationTimeSet

```solidity
event AllocationTimeSet(uint256 startTime, uint256 endTime)
```

===================== ======= Events ====== =====================



#### Parameters

| Name | Type | Description |
|---|---|---|
| startTime  | uint256 | undefined |
| endTime  | uint256 | undefined |

### Distributed

```solidity
event Distributed(address indexed recipientId, address recipientAddress, uint256 amount, address sender)
```

Event emitted when tokens are distributed



#### Parameters

| Name | Type | Description |
|---|---|---|
| recipientId `indexed` | address | undefined |
| recipientAddress  | address | undefined |
| amount  | uint256 | undefined |
| sender  | address | undefined |

### Initialized

```solidity
event Initialized(address allo, bytes32 profileId, uint256 poolId, bytes data)
```

Event emitted when strategy is initialized



#### Parameters

| Name | Type | Description |
|---|---|---|
| allo  | address | undefined |
| profileId  | bytes32 | undefined |
| poolId  | uint256 | undefined |
| data  | bytes | undefined |

### PoolActive

```solidity
event PoolActive(bool active)
```

Event emitted when pool is set to active status



#### Parameters

| Name | Type | Description |
|---|---|---|
| active  | bool | undefined |

### Registered

```solidity
event Registered(address indexed recipientId, bytes data, address sender)
```

Event emitted when a recipient is registered



#### Parameters

| Name | Type | Description |
|---|---|---|
| recipientId `indexed` | address | undefined |
| data  | bytes | undefined |
| sender  | address | undefined |



## Errors

### ALLOCATION_NOT_ACTIVE

```solidity
error ALLOCATION_NOT_ACTIVE()
```






### ALLOCATION_NOT_ENDED

```solidity
error ALLOCATION_NOT_ENDED()
```






### AMOUNT_MISMATCH

```solidity
error AMOUNT_MISMATCH()
```






### BaseStrategy_ALREADY_INITIALIZED

```solidity
error BaseStrategy_ALREADY_INITIALIZED()
```



*Returns when Base Strategy is already initialized*


### BaseStrategy_ARRAY_MISMATCH

```solidity
error BaseStrategy_ARRAY_MISMATCH()
```



*Returns when two arrays length are not equal*


### BaseStrategy_INVALID

```solidity
error BaseStrategy_INVALID()
```



*Returns as a general error when either a recipient address or an amount is invalid*


### BaseStrategy_INVALID_ADDRESS

```solidity
error BaseStrategy_INVALID_ADDRESS()
```



*Returns when an invalid address is used*


### BaseStrategy_NOT_INITIALIZED

```solidity
error BaseStrategy_NOT_INITIALIZED()
```



*Returns when Base Strategy is not initialized*


### BaseStrategy_POOL_ACTIVE

```solidity
error BaseStrategy_POOL_ACTIVE()
```



*Returns when a pool is already active*


### BaseStrategy_POOL_INACTIVE

```solidity
error BaseStrategy_POOL_INACTIVE()
```



*Returns when a pool is inactive*


### BaseStrategy_UNAUTHORIZED

```solidity
error BaseStrategy_UNAUTHORIZED()
```



*Returns when calls to Base Strategy are unauthorized*


### INVALID

```solidity
error INVALID()
```






### MAX_REACHED

```solidity
error MAX_REACHED()
```






### RECIPIENT_ERROR

```solidity
error RECIPIENT_ERROR(address recipientId)
```

===================== ======= Errors ====== =====================



#### Parameters

| Name | Type | Description |
|---|---|---|
| recipientId | address | undefined |

### UNAUTHORIZED

```solidity
error UNAUTHORIZED()
```






