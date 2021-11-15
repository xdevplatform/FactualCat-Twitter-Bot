# FactualCat Twitter Bot

[@FactualCat](https://twitter.com/FactualCat) is a Twitter Bot that Tweets cat facts daily. Built using the [manage Tweets ](https://developer.twitter.com/en/docs/twitter-api/tweets/manage-tweets/introduction)endpoint in the Twitter API v2 and deployed with Google [Cloud Functions](https://cloud.google.com/functions) and [Cloud Scheduler](https://cloud.google.com/scheduler). This bot parses cat facts from an API that provides cat facts, [catfact.ninja](https://catfact.ninja/), and Tweets them out.

There are two versions of this code sample in this repository:

- [cat_fact_bot.py](https://github.com/twitterdev/FactualCat-Twitter-Bot/blob/main/cat_fact_bot.py) - The Python code sample for testing locally
- [gcp_function.py](https://github.com/twitterdev/FactualCat-Twitter-Bot/blob/main/gcp_function.py) - The version of the code currently deployed to [Cloud Functions](https://cloud.google.com/functions). 

## Steps to running this code sample

### Step 1: Create your bot account

First, you will need to create a [new account](http://twitter.com/signup) for your bot 

### Step 2: Authenticate on behalf of your bot 

Before you can use the Twitter API v2, you will need a [developer account](https://developer.twitter.com/en/portal/petition/essential/basic-info). Once you have an a developer account, you will need to create a Project in the developer portal. Each Project contains an [App](https://developer.twitter.com/en/docs/basics/apps/overview), with which you can generate the credentials required to use the Twitter API. You can learn more about getting started with the Twitter API in the [getting started](https://developer.twitter.com/en/docs/getting-started) section of our documentation. You can apply for access from your main handle and authenticate on behalf of your account. 

To authenticate a new account, you can use a [pin-based OAuth flow](https://developer.twitter.com/en/docs/basics/authentication/overview/pin-based-oauth.html). There also is a helpful [forum post](https://twittercommunity.com/t/multiple-bot-accounts/128332) explaining how to authenticate on behalf of a bot account.

### Step 3: Setting up a Cloud Function

To set up a Cloud Function, you can follow a similar process outlined in the [Python quickstart ](https://cloud.google.com/functions/docs/quickstart-python)for Cloud Functions. You can first set your cloud region based on your location and select your trigger as “Cloud Pub/Sub” with a new topic. 

To avoid directly adding your keys and tokens to your Cloud Function, you can create [environment variables](https://cloud.google.com/functions/docs/configuring/env-var#cloud-console-ui_2). For example, under the “Runtime, build, connections and security settings“ header, you can set up environment variables for your Consumer Key, Consumer Secret, Access Token, and Access Token Secret. You can obtain these credentials in the developer portal, located in the “Keys and Tokens” page of the App inside your Project. 

After configuring your Cloud Function, you will see a page to set your runtime, the programming language, and the version you are using. This example uses Python 3.9 as the runtime environment. 
You can edit the `main.py` file that appears in the code editor to match the code found in [gcp_function.py](https://github.com/twitterdev/FactualCat-Twitter-Bot/blob/main/gcp_function.py). You also do the same for your [requirements.txt](https://github.com/twitterdev/FactualCat-Twitter-Bot/blob/main/requirements.txt) file.

### Step 4: Scheduling your Tweets with Cloud Scheduler 

After setting up your Cloud Function, you can use the [Cloud Scheduler](https://cloud.google.com/scheduler/docs/quickstart) to determine how often your bot will Tweet. For example, @FactualCat is currently Tweeting every 12 hours using the following notation: 

```
0 */12 * * *
```

## Support

* For general questions related to the API and features, please use the v2 section of our [developer community forums](https://twittercommunity.com/c/twitter-api/twitter-api-v2/65).

* If there's an bug or issue with the sample code itself, please create a [new issue](https://github.com/twitterdev/FactualCat-Twitter-Bot) here on GitHub.

* If you have questions about the future, check out these resources:
  * [Guide to the Future of the Twitter API](https://developer.twitter.com/en/products/twitter-api/early-access/guide)
  * [Twitter API Roadmap](https://t.co/roadmap)
  * [Twitter Developer Feedback](https://twitterdevfeedback.uservoice.com/forums/930250-twitter-api), where you can post and vote on ideas and feature requests

## Contributing

We welcome pull requests that add meaningful additions to these code samples, particularly for languages that are not yet represented here.

We feel that a welcoming community is important and we ask that you follow Twitter's [Open Source Code of Conduct](https://github.com/twitter/code-of-conduct/blob/master/code-of-conduct.md) in all interactions with the community.

## License

Copyright 2021 Twitter, Inc.

Licensed under the Apache License, Version 2.0: https://www.apache.org/licenses/LICENSE-2.0
