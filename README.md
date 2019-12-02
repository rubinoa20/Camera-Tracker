#include <kipr/botball.h>
int orange = 0;
int servo = 0;
int right = 10;
int left = 2040;
int reset = 1024;
int l_motor = 0; 
int r_motor = 3;
int forward = 55;
int backward = -55;
int pause = 1000;

int main()
{
camera_open();
enable_servos();
    
int servo_pos = 1024;
set_servo_position(0,1024);
    
while (digital(8) == 0)
{
camera_update();
if (get_object_count(orange) > 0)
{
	int updated_pos = get_object_center_x (orange, 0) * 7.5;
    set_servo_position(3, updated_pos);
    msleep(20);
    printf("updated_pos = %d/n", updated_pos);
    }
    else
    {
        printf("No Orange Detected/n");
    }
}
camera_close();
disable_servos();
return 0;
}
