# PMU_Kovalenko_VPR42
**Листинг 5.9. Класс TimePickFragment (файл ТimePickFragment.(Java)**

> package cm.example.ch05time;
>
> import android.app.AlertDialog; import android.app.Dialog;
>
> import android.app.TimePickerDialog; import
> android.content.DialogInterface; import android.os.Bundle;
>
> import android.support.v4.app.DialogFragment; import
> android.widget.Button;
>
> import android.widget.TextView; import android.widget.TimePicker;
>
> import java.util.Calendar;
>
> public class TimePickFragment extends DialogFragment implements
> TimePickerDialog.OnTimeSetListener (
>
> \@Override
>
> public Dialog onCreateDia1og(Bundle savedInstanceState) (
>
> // yciaHaBmeaem iexyuee **Bpews** Asx TimePicker final Calendar c =
> Calendar.getInstance(); int hour = c.get(Calendar.HOUR_OF_DAY);
>
> int minute = c.get(Calendar.MINUTE);
>
> *135*
>
> // cosAam TimePickerDialog x sosBpauaeu ero

Dialog picker = new TimePickerDialog(getActivity(), this, hour, minute,

true);

> picker.setTitle(getResources().getString(R.string.choose_time));
> return picker;
>
> \@Override
>
> public void onstart() ( super.onStart();
>
> // nOOaBnneu nons soBamenscxxñ mexcz can iuionxx
>
> Button nButton = ((AlertDialog)
>
> getDialog()).getButton(DialogInterface.BUTTON_POSITIVE):
> nButton.setText(getResources().getString(R.string.ready));
>
> \@Override
>
> public void onTimeSet(TimePicker view, int hours, int minute) {
>
> **// sssOQMM BNO@aHHoe** spemA
>
> TextView tv = (TextView) getActivity().findViewById(R.id.tv);
>
> *136 Uacma Il.* 6aooeoe npoapa»‹»iz/poeanz/e *önn Android*
>
> tv.setText(getResources().getString(R.string.hours) + hours
>
> \+ getResources().getString(R.string.minutes) + minute);
>
> Разметка (Файл activity_main.xml) будет почти такой же (листинг 5.10).

![](vertopal_ec5adb6936a94f3995f00a8d3334805c/media/image1.png){width="5.52in"
height="0.24333223972003498in"}

> \<RelativeLayout
> [xmlns:android=\"http://schemas.android.com/apk/res/android\"](http://schemas.android.com/apk/res/android)
> [xmlns:tools=\"http://schemas.android.com/tools\"](http://schemas.android.com/tools)
> android:layout_width=\"match_parent\"
> android:layout_height=\"match_parent\"
>
> \<TextView
>
> android:text=\"0string/app_name\"
> android:layout_width=\"wrap_content\"
> android:layout_height=\"wrap_content\" android:textSize=\"22sp\"
> android:id=\"@+id/tv\" /\>
>
> \<Button
>
> android:layout_width=\"wrap_content\"
> android:layout_height=\"wrap_content\" android:text=\"yciaHOsxie
> specs\" android:id=\"@+id/button\" android:layout_below=\"@+id/tv\"
> android:layout_alignParentLeft=\"true\"
> android:layout_alignParentStart=\"true\"
> android:layout_marginTop=\"ll6dp\" android:textSize=\"22sp\"
> android:onClick=\"onClick\"/\>
>
> \</RelativeLayout\>

##### OczanOGb TOJIsxo onpe,genirrs xon MainActivity.java (oxGTHiir 5.11).

![](vertopal_ec5adb6936a94f3995f00a8d3334805c/media/image2.png){width="5.52in"
height="0.24333223972003498in"}

> package com.example.ch05time;
>
> import android.support.v7.app.AppCompatActivity; import
> android.os.Bundle;
>
> import android.support.v4.app.DialogFragment; import
> android.view.View;
>
> Tnaea 5. Veeöouneøun, dua/zoaoesie oxxa u uau/o
>
> public class NainActivity extends AppCompatActivity ( ßOverride
>
> protected void onCreate(Bundle savedInstanceState) {
> super.onCreate(savedInstanceState);
> setContentView(R.layout.activity_main);
>
> public void onClick(View v) (
>
> DialogFragment newFragment = new TimePickFragment();
> newFragment.show(getSupportFragmentManager(), \"timePicker");

![](vertopal_ec5adb6936a94f3995f00a8d3334805c/media/image3.jpeg){width="3.1666666666666665in"
height="4.593055555555556in"}В отличие от диалогового окна выбора даты,
выбранное время не требует никаких поправок, и надпись отобразит именно
то, что вы выбрали (рис. 5.8).

> 5.3. Меню

Уведомления и диалоговые окна--- это хорошо, но редко какое приложение
обхо­дится без меню.

Меню являются стандартными компонентами пользовательского интерфейса в
приложениях многих типов. Для обеспечения привычной и единообразной
техно­логии работы с приложением следует представлять действия
пользователя и другие варианты выбора в своих операциях с помощью
АР1-интерфейсов класса **Menu.**

В устройствах, работающих под управлением Android, начиная с версии
Android **3.0** (уровень АР1 **11),** наличие отдельной кнопки **Меню**
больше не требуется. С учетом этого изменения приложения для АпбгоЫ
более не должны зависеть от традиционной панели меню из 6 пунктов.
Вместо нее в них должна присутствовать строка действий с часто
используемыми действиями пользователя.

> Операционная система Android предлагает три вида меню:

-   меню параметров (Options Menu) --- это основное меню приложения,
    > здесь сле­дует размещать пункты, затрагивающее приложение в целом:
    > **Настройка, Соз­дать, Поиск** и пр.

-   контекстное меню (Соп1ех1 Menu) --- это меню появляется при долгом
    > касании (2 или более секунды) сенсорного экрана;

-   всплывающее меню или подменю (Submenu) --- оно привязывается к
    > конкрет­ному пункту меню (меню параметров или контекстного меню).
    > Пункты подме­ню не поддерживают вложенное меню.

> 5.3.1. Определение меню в ХМL-файле

С учетом того, что меню более не ограничено шестью пунктами и может
содержать гораздо больше команд, проще определять команды меню в
ХМЬ-файле, который находится в папке **\\rеz\\menu\\.** Использовать
ХМL-файлы (а не определять команды меню в .javа-коде) рекомендуется по
нескольким причинам:

-   в ХМЬ проще визуализировать структуру меню;

-   это позволяет отделить контент для меню от кода, определяющего
    > работу при­ложения;

-   это позволяет создавать альтернативные варианты меню для разных
    > версий платформы, размеров экрана и других конфигураций путем
    > использования структуры ресурсов приложения.

> Вернемся к ХМЬ-файлу. Он должен содержать следующие элементы:

-   **\<menu\>** --- определяет класс **menu,** являющийся контейнером
    > для пунктов меню. Элемент **\<menu\>** должен быть корневым узлом
    > файла, в котором может нахо­диться один или несколько элементов
    > **\<item\>** и **\<group\>;**

-   \<item\> --- представляет один пункт меню. Элемент может содержать
    > вложенный элемент **\<group\>** для создания подменю;

> **□ \<group\>**--- невидимый контейнер для элементов **\<item\>.**
> Позволяет разделять пункты меню на категории и назначать им одинаковые
> свойства--- например, видимость, активное состояние.

В листинге 5.12 приведен пример файла та1п_тепи.хш1, описывающего меню
при­ложения.

**[Листинг 5.12.]{.smallcaps} Меню приложения (файл main_menu.xml)**

> \<?xml version=\"l.0\" encoding=\"utf-8\"?\>
>
> \<menu
> [xmlns:android=\"http://schemas.android.com/apk/res/android\"\>](http://schemas.android.com/apk/res/android)
>
> \<item android:id=\"@+id/new_game\"
> android:icon=\"@drawable/ic_new_game\"
> android:title=\"@string/new_game\" android:showAsAction=\"ifRoom\"/\>
>
> \<item android:id=\"ê+id/help\" android:icon=\"@drawable/ic_help\"
> android:title=\"@string/help\" /\>

##### \</menu\>

Элемент \<item\> поддерживает несколько атрибутов, с помощью которых
можно определить внешний вид и поведение пункта меню. Пункты
приведенного в лис­тинге 5.12 меню имеют следующие атрибуты:

> О android:id--- идентификатор ресурса, который является уникальным для
> этого пункта, что позволяет приложению распознавать пункт, когда его
> выбирает пользователь;

-   **android:**1**соп** --- ссылка на графический элемент, который
    > будет использоваться в качестве значка пункта меню;

> О android: title --- ссылка на строку, которая будет использоваться в
> качестве на­звания пункта меню;

-   android: ShowAction --- указывает, когда и как этот пункт должен
    > отображаться в строке действий.

Это самые важные атрибуты, но при желании в Android SDK вы можете
ознако­миться и с другими атрибутами.

К пункту любого меню (кроме вложенного) можно добавить вложенное меню
или подменю. Для этого нужно добавить элемент **\<menu\>** в качестве
дочернего элемента **\<item\>** (листинг 5.13).

**[Листинг]{.smallcaps} 5,13. Определение подменю**

> \<?xml version=\"l.0\" encoding=\"utf-8\"?\>
>
> \<menu
> [xmlns:android=\"http://schemas.android.com/apk/res/android\"\>](http://schemas.android.com/apk/res/android)
>
> \<item android:id=\"ß+id/file\" android:title=\"Østring/file\" \>
>
> *140*
>
> \<!\-- \"file\" submenu \--\>
>
> \<menu\>
>
> \<item android:id=\"@+id/create_new\"
> android:title=\"@string/create_new\" /\>
>
> \<item android:id=\"@+id/open\" android:title=\"ßstring/open\" /\>
>
> \</menu\>

#### ‹/item\>

> \</menu\>

5.3.2. Создание основного меню (меню параметров)

Как уже отмечалось, в основном меню размещаются команды, затрагивающие
при­ложение в целом. Место, где будет отображено это меню, зависит только
от версии Android, и сами вы не можете повлиять на его расположение.

Объявлять пункты меню параметров можно либо из подкласса Activity, либо
из подкласса Fragment. Если и ваша операция, и фрагменты объявляют
пункты меню параметров, в пользовательском интерфейсе они объединяются.
При этом сначала отображаются пункты операции, а за ними следуют пункты
фрагментов в том по­рядке, в котором каждый фрагмент добавляется в
операцию. При необходимости можно изменить порядок следования пунктов
меню с помощью атрибута Android: orderInCategoryуказываемого в каждом
элементе item\>, который требу­ется переместить.

Чтобы указать меню параметров для операции, следует переопределить метод
onCreateOptionsMeny(). В этом методе можно загрузить В класс Menu
собственный ресурс меню, заблаговременно определенный в ХМL:

> Ooverride
>
> public boolean onCreateOptionsMenu(Menu menu) ( MenuInflater inflater
> = getMenuInflater(); inflater.inflate(R.menu.main_menu, menu); return
> true;

Пункты меню также можно добавлять с помощью метода add(), а получать их
с помощью метода FindItemО для пересмотра свойств этих пунктов с помощью
АР1-интерфейсов MenuItem. Именно метод ас!с1() использовался в
предыдущем из­дании этой книги:

> public static final int IDM_NEW = 101;
>
> public static final int IDM_OPEN = 102; public static final int
> IDM_SAVE = 103; public static final int IDM EXIT = 104;
>
> ßOverride
>
> public boolean onCreateQptionsMenu(Menu menu) (
>
> // CosAam nyHxma uenD
>
> menu.add(Menu.NONE, IDM NEW, Nenu.NONE, \"New\");
>
> Fnaea ***5. Уведомления и диалоговые окна***
>
> menu . add (Nenu . NCNE, I Et\'1_OPEN, Nenu . NONE, \"Open\" ) i menu
> . add tNenu . NObfE, I D1•i_SAVE, Nenu . NONE, • Save\" ) i menu. add
> (Nenu . NObiE, I Df•i_EXIT, Nenu . NONE, \"Exit\" ) i
>
> return(super.onCreateOptionsNenu(menu));

Если пунктов меню немного, вы можете использовать метод аасИ). А во всех
остальных случаях удобнее использовать ХМL-файл.

Теперь поговорим об обработке нажатий. Наши пункты меню уже
отображаются, но пока ничего не делают, поскольку обработчики событий
еще не заданы. Когда пользователь выбирает пункт меню параметров,
система вызывает метод onOptionsItemSelected(). Этот метод передает
выбранный класс MenuItem. Иденти­фицировать пункт меню можно, вызвав
метод getItemId(), который возвращает уникальный идентификатор пункта
меню (определенный атрибутом android:id) из ресурса меню или целым
числом, переданным методу асмо). Этот идентификатор можно сопоставить с
известными пунктами меню, чтобы выполнить соответст­вующее действие.
Рассмотрим пример:

> \@Override
>
> public boolean onOptionsItemSelected(NenuItem item) {
>
> **// Oopa6aTbsaea** Bs6pdxHoe AeñciBxe
>
> switch (item.getItemId()) { case R.id.new_game:
>
> newGame();
>
> return true;
>
> case R.id.help: showHelp(); return true;
>
> default:
>
> return super.onOptionsItemSelected(item);

**[Если]{.smallcaps}** вы использовали метод add(), то распознать, какая
команда была выбрана пользователем, можно так:

> switch (item.getItemId()) {
>
> . case IDM_NEW: t = \"New selected\"; break; case IDM_OPEN: t = \"Open
> selected\"; break; case IDM_SAVE: t = "Save selected\"; break; case
> IDM_EXIT: t = "Exit selected\"; break; default: return false;

Это также делается в методе onOptionsItemSelected().

Начиная с Android 3.0, появилась возможность с помощью атрибута android:
onclick oпределять в ХМL поведение для пунктов меню при нажатии на них.
Значением
