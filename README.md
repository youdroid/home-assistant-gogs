[![Validate with hassfest](https://github.com/youdroid/home-assistant-gogs/actions/workflows/hassfest.yml/badge.svg)](https://github.com/youdroid/home-assistant-gogs/actions/workflows/hassfest.yml) [![Validate with HACS](https://github.com/youdroid/home-assistant-gogs/actions/workflows/validate.yaml/badge.svg)](https://github.com/youdroid/home-assistant-gogs/actions/workflows/validate.yaml)
# Gogs repository tracker

Home Assistant component to feed Home Assistant component to feed all your repositories on Gogs.

## Installation
1. Install this component by copying [these files](https://github.com/youdroid/home-assistant-gogs/tree/master/custom_components/gogs) to `custom_components/gogs/`.
2. Install the card: [Entity attributes](https://github.com/custom-cards/entity-attributes-card)
3. Add the code to your `configuration.yaml` using the config options below.
4. Add the card code to your `ui-lovelace.yaml`. 
5. **You will need to restart after installation for the component to start working.**

### Options

| key | default | required | description
| --- | --- | --- | ---
| token | | yes | Your Gogs token [(Find your Gogs token)](https://www.jetbrains.com/help/youtrack/standalone/integrate-project-with-gogs.html#enable-youtrack-integration-gogs)
| host |  | yes | The host which Gogs is running on.
| protocol |  | yes | The HTTP protocol used by Gogs.
| port |  | yes | The port which Gogs is running on.
| repositories |  | yes | A List of your repositores you want to track that contain repository path.

## Exemples

### Example for minimal config needed in configuration.yaml:
```yaml
    sensor:
      - platform: gogs
        token: YOUR_GOGS_TOKEN
        host: localhost
        protocol: http
        port: 80
        repositories:
          - path: 'user/crazy_repo'
```
### Example for ui-lovelace.yaml:
```yaml
    - type: custom:entity-attributes-card
      title: gogs repository 
       heading_name: Attributes
       heading_state: States
       filter:
         include:
           - key: sensor.gogs_crazy_repo.*
```
### Multiple repositories for configuration.yaml:
```yaml
    sensor:
      - platform: gogs
        token: YOUR_GOGS_TOKEN
        host: localhost
        protocol: http
        port: 80
        repositories:
          - path: 'user/crazy_repo'
          - path: 'user/awesome_repo'
          - path: 'user/amazing _repo'

```