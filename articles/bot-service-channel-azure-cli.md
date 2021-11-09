---
title: Connect your bot to channels with Azure CLI
description: This sample shows Azure CLI commands for connecting your bot to a communication application, such as email, Facebook, or the Kik messaging app.
ms.topic: how-to
author: JonathanFingold
ms.author: kamrani
ms.date: 08/06/2021
ms.service: bot-service
ms.custom: devx-track-azurecli
---

# Connect your bot to channels with Azure CLI

A channel is a connection between a communication application and a bot. A bot, registered with Azure, uses channels to enable communication with users. The commands in this article connect a bot to various channels. For more information, see [Connect a bot to channels](bot-service-manage-channels.md).

[!INCLUDE [Prepare your Azure CLI environment](includes/azure-cli-prepare-your-environment.md)]

- A bot deployed to Azure. Refer to [Create a bot with the Bot Framework SDK](bot-service-quickstart-create-bot.md) and [Deploy a basic bot](v4sdk/bot-builder-tutorial-deploy-basic-bot.md).

## Sample commands

The following sections use Azure CLI commands to connect a bot to a channel. These examples use a bot named `ContosoBot` in the `ContosoBotRG` resource group.

Some of these channels require the command to connect with the application to authenticate. If you're running these commands for testing purposes, they can fail if you don't use real values.

### Direct Line

Direct Line integrates your bot into a mobile app, web page, or other applications. For more information, see [About Direct Line](bot-service-channel-directline.md).

These sample commands create a connection to the Direct Line channel by using [az bot directline create](/cli/azure/bot/directline#az_bot_directline_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot directline create --resource-group ContosoBotRG --name ContosoBot --disablev1
az bot directline show --resource-group ContosoBotRG --name ContosoBot
az bot directline delete --resource-group ContosoBotRG --name ContosoBot
```

### Office 365 email

You can enable your bot to communicate with users by using Office 365 email. For more information, see [Connect a bot to Office 365 email](bot-service-channel-connect-email.md).

These sample commands create a connection to the channel for Office 365 email by using [az bot email create](/cli/azure/bot/email#az_bot_email_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot email create --resource-group ContosoBotRG --name ContosoBot \
   --email-address ContosoBot@outlook.com --password <password>
az bot email show --resource-group ContosoBotRG --name ContosoBot
az bot email delete --resource-group ContosoBotRG --name ContosoBot
```

### Facebook

You can connect your bot to both Facebook Messenger and Facebook Workplace. It can communicate with users on both platforms. For more information, see [Connect a bot to Facebook](bot-service-channel-connect-facebook.md).

These sample commands create a connection to the channel for Facebook by using [az bot facebook create](/cli/azure/bot/facebook#az_bot_facebook_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot facebook create --resource-group ContosoBotRG --name ContosoBot --appid <myAppId> \
   --page-id <myPageId> --secret <secret> --token <token>
az bot facebook show --resource-group ContosoBotRG --name ContosoBot
az bot facebook delete --resource-group ContosoBotRG --name ContosoBot 
```

### Kik

You can configure your bot to communicate through the Kik messaging app. For more information, see [Connect a bot to Kik](bot-service-channel-connect-kik.md).

These sample commands create a connection to the channel for the Kik app by using [az bot kik create](/cli/azure/bot/kik#az_bot_kik_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot kik create --resource-group ContosoBotRG --name ContosoBot --user-name <mykikname> \
   --key <key> --is-validated false
az bot kik show --resource-group ContosoBotRG --name ContosoBot
az bot kik delete --resource-group ContosoBotRG --name ContosoBot
```

### Microsoft Teams

You can configure your bot to communicate with Microsoft Teams. For more information, see [Connect a bot to Microsoft Teams](channel-connect-teams.md).

These sample commands create a connection to the channel for Microsoft Teams by using [az bot msteams create](/cli/azure/bot/mstreams#az_bot_msteams_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot msteams create --resource-group ContosoBotRG --name ContosoBot --calling-web-hook https://www.contosoapp.com/ \
   --enable-calling 
az bot msteams show --resource-group ContosoBotRG --name ContosoBot 
az bot msteams delete --resource-group ContosoBotRG --name ContosoBot
```

### Skype

You can configure your bot to communicate with Skype. For more information, see [Connect a bot to Skype](bot-service-channel-connect-skype.md).

These sample commands create a connection to the channel for Skype by using [az bot skype create](/cli/azure/bot/skype#az_bot_skype_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot skype create --resource-group ContosoBotRG --name ContosoBot --enable-messaging --enable-screen-sharing
az bot skype show --resource-group ContosoBotRG --name ContosoBot 
az bot skype delete --resource-group ContosoBotRG --name ContosoBot
```

### Slack

You can configure your bot to communicate with users through Slack. For more information, see [Connect a bot to Slack](bot-service-channel-connect-slack.md).

These sample commands create a connection to the channel for Slack by using [az bot slack create](/cli/azure/bot/slack#az_bot_slack_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot slack create --resource-group ContosoBotRG --name ContosoBot --client-id <clientid> \
   --client-secret <secret> --verification-token <token>
az bot slack show --resource-group ContosoBotRG --name ContosoBot
az bot slack delete --resource-group ContosoBotRG --name ContosoBot
```

### SMS

These sample commands create a connection to the channel for SMS by using [az bot sms create](/cli/azure/bot/sms#az_bot_sms_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot sms create --resource-group ContosoBotRG --name ContosoBot --account-sid <sid> --auth-token <token> \
   --phone <smsphonenumber> --is-validated
az bot sms show --resource-group BotRG
az bot sms delete --resource-group BotRG
```

### Telegram

You can configure your bot to communicate with users through Telegram. For more information, see [Connect a bot to Telegram](bot-service-channel-connect-telegram.md).

These sample commands create a connection to the channel for Telegram by using [az bot telegram create](/cli/azure/bot/telegram#az_bot_telegram_create). The example shows the connection in the console and deletes the connection.

```azurecli
az bot telegram create --resource-group ContosoBotRG --name ContosoBot --access-token <token> --is-validated
az bot telegram show --resource-group ContosoBotRG --name ContosoBot 
az bot telegram delete --resource-group ContosoBotRG --name ContosoBot 
```

## Clean up deployment

If you created a resource group for testing, run the [az group delete](/cli/azure/group#az_group_delete) command to remove the resource group and everything it contains.

```azurecli
az group delete --name ContosoBotRG
```

To remove a connection to a channel, use the appropriate delete command.

## Azure CLI commands used in this article

This article uses the following Azure CLI commands:

- [az bot directline create](/cli/azure/bot/directline#az_bot_directline_create)
- [az bot directline delete](/cli/azure/bot/directline#az_bot_directline_delete)
- [az bot directline show](/cli/azure/bot/directline#az_bot_directline_show)
- [az bot email create](/cli/azure/bot/email#az_bot_email_create)
- [az bot email delete](/cli/azure/bot/email#az_bot_email_delete)
- [az bot email show](/cli/azure/bot/email#az_bot_email_show)
- [az bot facebook create](/cli/azure/bot/facebook#az_bot_facebook_create)
- [az bot facebook delete](/cli/azure/bot/facebook#az_bot_facebook_delete)
- [az bot facebook show](/cli/azure/bot/facebook#az_bot_facebook_show)
- [az bot kik create](/cli/azure/bot/kik#az_bot_kik_create)
- [az bot kik delete](/cli/azure/bot/kik#az_bot_kik_delete)
- [az bot kik show](/cli/azure/bot/kik#az_bot_kik_show)
- [az bot msteams create](/cli/azure/bot/mstreams#az_bot_msteams_create)
- [az bot msteams delete](/cli/azure/bot/mstreams#az_bot_msteams_delete)
- [az bot msteams show](/cli/azure/bot/mstreams#az_bot_msteams_show)
- [az bot skype create](/cli/azure/bot/skype#az_bot_skype_create)
- [az bot skype delete](/cli/azure/bot/skype#az_bot_skype_delete)
- [az bot skype show](/cli/azure/bot/skype#az_bot_skype_show)
- [az bot slack create](/cli/azure/bot/slack#az_bot_slack_create)
- [az bot slack delete](/cli/azure/bot/slack#az_bot_slack_delete)
- [az bot slack show](/cli/azure/bot/slack#az_bot_slack_show)
- [az bot sms create](/cli/azure/bot/sms#az_bot_sms_create)
- [az bot sms delete](/cli/azure/bot/sms#az_bot_sms_delete)
- [az bot sms show](/cli/azure/bot/sms#az_bot_sms_show)
- [az bot telegram create](/cli/azure/bot/telegram#az_bot_telegram_create)
- [az bot telegram delete](/cli/azure/bot/telegram#az_bot_telegram_delete)
- [az bot telegram show](/cli/azure/bot/telegram#az_bot_telegram_show)
- [az group delete](/cli/azure/group#az_group_delete)

## Next steps

- [Connect a bot to channels](bot-service-manage-channels.md)
- [Manage a bot](bot-service-manage-overview.md)