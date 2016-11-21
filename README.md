# BOSH Release for Elastalert

This is a BOSH release for [elastalert] (https://github.com/Yelp/elastalert), the framework for alerting on data and logs in Elasticsearch.

## Prerequisite

The release has been tested with
- [Logsearch] (https://github.com/cloudfoundry-community/logsearch-boshrelease.git) v203.0.0 (Kibana v4.4)
- [Elastalert] (https://github.com/cloudfoundry-community/docker-boshrelease)  v0.1.1
- [Spiff] (https://github.com/cloudfoundry-incubator/spiff)
- Internet access / without Internet access with [precompiled release] (https://github.com/orange-cloudfoundry/elastalert-boshrelease/tree/master/precompiled_releases)

## Usage

To use this bosh release, first upload it to your bosh:

```
bosh target BOSH_HOST
git clone https://github.com/orange-cloudfoundry/elastalert-boshrelease.git
cd elastalert-boshrelease
bosh upload release releases/elastalert/elastalert-{latest}.yml
```

## Deployment Manifests and Deploy

To create your stub manifest you can use our openstack example under examples/stub.yml.

For Openstack you can quickly create a deployment manifest & deploy:

```
./scripts/generate_deployment_manifest openstack FULL_PATH_TO_YOUR_STUB_MANIFEST > FULL_PATH_TO_FINAL_MANIFEST
bosh deployment FULL_PATH_TO_FINAL_MANIFEST
bosh -n deploy
```

## Development

Inspired by the project [elastalert] (https://github.com/Yelp/elastalert) we created a BOSH release to alert by email on rules as follows:
- any
- change
- frequency
- spike
- flatline
- new term
- cardinality

More details could be found [here] (https://github.com/orange-cloudfoundry/elastalert-boshrelease/tree/master/jobs/elastalert).

To compile this release an Internet access is required. If not, a http(s)_proxy config could be used, or there is a precompiled BOSH release available.