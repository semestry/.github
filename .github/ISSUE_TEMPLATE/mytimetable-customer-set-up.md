---
name: MyTimetable customer set up
about: Configure MyTimetable for a specific customer.
title: CUSTOMER MyTimetable configuration
labels: 'Type: Customer Impl.'
assignees: ''

---

## Customer

Which customer needs to be set up?

## Tasks

- [ ] Set the ext.customer string in the main `build.gradle` file to the unique customer id.
- [ ] Comment out all development config in `config/development/mytimetable-core.properties`.
- [ ] Configure the customer specific user preferences database in `config/customer/mytimetable-core.properties`.
- [ ] Configure the supported locales:
    - [ ] By setting the Locales property in `config/customer/mytimetable-core.properties`.
    - [ ] Update locales included (twice) in GWT compile in `mytimetable-web-gwt\src\main\resources\nl\eveoh\mytimetable\web\MyTimetable.gwt.xml` if necessary. Also make sure to set the correct fallback locale if not `en_GB`.
    - [ ] Add/remove unsupported locales in `mytimetable-web-gwt\src\main\resources\nl\eveoh\mytimetable\web\str.js`.
- [ ] For non-Dutch customers, configure the timezone:
    - [ ] Set the property `Timezone` in `config/customer/mytimetable-web-server.properties`.
    - [ ] Set the property `TargetTimeZoneJson` in `config/customer/mytimetable-web-server.properties`.
    - [ ] Adjust the `TimezoneDialogBox_amsterdamTimeZoneRadioButton` property in the resource bundles.
- [ ] Configure the `IcalUidPostfix` property in `config/customer/mytimetable-web-server.properties`.
- [ ] Set `ical.redirectInsecure` to `false` for new customer installs, to prevent HTTP iCal requests.
- [ ] Set `saml.signature_algorithm = sha256` if customer uses SAML.
- [ ] Set `CustomerName` in the `ResourceBundle.properties` and translations
- [ ] Set `PrivacyPolicy.Url` in the properties
- [ ] For managed hosting: modify `PrivacyPolicy.Categories` in the properties, including translations
- [ ] If desired, customize the brand name by adjusting `MyTimetable_Brand` in the resource bundles.
- [ ] Replace the various favicons in `mytimetable-web-server\src\main\resources\static\assets\images`.
- [ ] Style the GWT interface:
    - [ ] Adjust values in `mytimetable-web-gwt\src\main\resources\nl\eveoh\mytimetable\web\gwt\css\variables.css`.
    - [ ] Add the logos as `logo-<customer_id>.png` and `logo-<customer_id>@2x.png` to `mytimetable-web-server\src\main\resources\static\assets\images` and configure `HeaderPanel_headerImage_src = /assets/images/logo-<customer_id>.png` and `HeaderPanel_headerImage_retinaSrc`.
    - [ ] Configure `HeaderPanel_headerImage_link` to point to the corporate website (mind scheme and `www.`, to avoid unnecessary redirects) in `config/customer/mytimetable-web-server.properties`.
    - [ ] If absolutely necessary, you can use `mytimetable-web-gwt\src\main\resources\nl\eveoh\mytimetable\web\gwt\css\scheduleviewer-client.css` to override CSS classes.
- [ ] Style the mobile interface:
    - [ ] Override variables in `mytimetable-web-mobile\src\main\resources\static\assets\m\resources\sass\client\_overrides.scss`.
    - [ ] Adjust `Mobile_ThemeColor` and `WindowsPhone_TileColor` in the default resource bundle.
- [ ] Style the Bootstrap based pages:
    - [ ] Override variables in `mytimetable-web-server-shared\src\main\resources\static\assets\sass\bootstrap\client\_overrides.scss`.
    - [ ] Add the emblems in `mytimetable-web-server-shared\src\main\resources\static\assets\images` and configure it by setting the properties `Branding.Emblem.Src` and `Branding.Emblem.RetinaSrc` in `config/customer/mytimetable-web-server.properties`.
- [ ] Customize the login page, if required.
- [ ] Adjust resource bundles whenever necessary.
- [ ] Adjust configuration in `config/customer/**` and `**/*.override.xml` whenever necessary.

## Additional context

Is a development database available? Is there any documentation on customer specific configuration required? Where can logos and emblems be found?

## Acceptance criteria

- [ ] The MyTimetable release has been deployed to the acceptance environment of the customer.
- [ ] Deployment of the new version has been communicated to the customer.

