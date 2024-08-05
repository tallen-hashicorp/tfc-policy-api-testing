# tfc-policy-api-testing
Testing some TFC API Calls

## Set Token
* Login to TFC
* Click User icon (Top Right) and select Account Settings
* Select Tokens
* Click Create an API token
* Copy the token
* Run the following command replacing `my-token` with your token
* `export TOKEN=my-token``

## Select the org
In order for the following commands to work you need to set your organizations name as an envrioment variable, run the folllowing replacing `my-org` with your org name
```bash
export ORG=my-org
```

## Get Policy Set
This also shows the polices included in the set however only thir ID and type
```bash
curl \
  -k \
  --header "Authorization: Bearer $TOKEN" \
  https://app.terraform.io/api/v2/organizations/$ORG/policy-sets | jq
```

[example output](example_outputs/get_policy_set.json)

## Get Policy Set with policies included
This has an extra field included which contains all the polices
```bash
curl \
  -k \
  --header "Authorization: Bearer $TOKEN" \
  https://app.terraform.io/api/v2/organizations/$ORG/policy-sets?include=policies | jq
```

[example output](example_outputs/get_policy_set_include_policies.json)

## Get Policy
This lists all policies in an org
```bash
curl \
  -k \
  --header "Authorization: Bearer $TOKEN" \
  https://app.terraform.io/api/v2/organizations/$ORG/policies | jq
```

[example output](example_outputs/get_policy.json)

## Get a policy based on ID
Replace `policy_id` with your policy id. 
```bash
export POLICY_ID=policy_id
curl \
  -k \
  --header "Authorization: Bearer $TOKEN" \
  https://app.terraform.io/api/v2/policies/$POLICY_ID | jq
```

[example output](example_outputs/policy.json)